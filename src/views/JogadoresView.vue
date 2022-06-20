  <script>
  import {v4 as uuidv4} from "uuid"
 export default {
   data() {
     return {
       jogadores: [
         {id: 'd4ce72f7-1971-4107-9c80-77d021dd63ea', nome: 'Carol', time: 'Praia Clube'},
         {id: 'b2f0af2d-e110-4a9a-8c95-3fea7dd68653', nome: 'Mayany', time: 'Sesi/Bauru'},
         {id: '539782c5-da35-4612-9323-d6687a584479', nome: 'Julia', time: 'Minas'},
         {id: 'e8c96c5b-4e96-4eec-93f8-b43b351e4a27', nome: 'Pri Daroit', time: 'Minas'},    
         {id: 'a1f5e3d3-5d04-46f5-bc6f-185d46a28993', nome: 'Nyeme', time:'Sesi/Bauru'}
        ],
        novo_jogador: "",
        novo_time: "exemplo",
     };
   },
   methods: {
     salvar() {
       if (this.novo_jogador !== ""){}
       const novo_id = uuidv4();
       this.jogadores.push({
         id: novo_id,
         nome: this.novo_jogador,
         time: this.novo_time
       });
       this.novo_jogador = "";
     },
     excluir(jogadores){
    const indice = this.jogadores.indexOf(jogadores);
    this.jogadores.splice(indice, 1)
  },
   },
 };
  </script>
  <template>
  <main>
    <div class="container">
      <div class="title">
        <h2>Gerenciamento de Jogadores</h2>
      </div>
      <div class="form-input">
        <input type="text" v-model="novo_jogador" />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-jogadores">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Nome</th>
              <th>Ações</th>
              <th>Time</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="jogadores in jogadores" :key="jogadores.id">
              <td>{{jogadores.id}}</td>
              <td>{{jogadores.nome}}</td>
              <td>
              <button>Editar</button>
              <button @click="excluir(jogadores)">Excluir</button>
              </td>
              <td>{{jogadores.time}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
</template>
<style>
.title {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}
.form-input {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}
.form-input input {
  width: 60%;
  height: 40px;
  border: 1px solid rgb(147, 147, 147);
  border-radius: 10px;
  padding: 0 10px;
}
.form-input button {
  margin-left: 1px;
  width: 20%;
  height: 40px;
  border: 1px solid rgb(211, 211, 211);
  border-radius: 10px;
  background-color: #d194e0;
  color: rgb(255, 255, 255);
  font-weight: bold;
  cursor: pointer;
}
.list-jogadores{
  display: flex;
  justify-content: center;
}
.list-jogadores table{
  width: 80%;
  margin: 0 auto;
  border-collapse: collapse;
}
table tr td{
  border: 1px solid rgb(211, 211, 211);
  padding: 10px;
}
</style>
