<template>
  <div> 
    <h1 :class= "{'title':true, 'title-home':isHome}">
      CURSO 3D
    </h1>
    <p :class="['text','title']">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum fuga modi provident iusto! Temporibus obcaecati accusamus earum blanditiis reprehenderit quos explicabo quisquam necessitatibus, tempora sequi, fugit, quam possimus praesentium cumque.
    </p>

    <!-- utilizando o v-show para controlar quando o Header será mostrado -->
    <MyHeader
      v-show="showHeader"
    />
    <!-- ---------------------------------------------------------------- -->
    
    <!-- Separa por nivel de acesso no sistema utilizando o (v-if, v-else-if e v-else) -->
    <div v-if="acessLevel === 'admin'"> Admin </div>
    <div v-else-if="acessLevel === 'marketing'"> Marketing </div>
    <div v-else> User </div>

    <!-- verifica se a condição ShowName é true ou false -->
    <div v-show="showName">
        Nome: {{firstName}} <br>
        Sobrenome: {{ lastName }} 
    </div>
    <!-- ------------------------------------------------ -->

    <!-- CRIA UMA LISTA DE VALORES ATRAVÉS DO v-for, ONDE OS VALORES SÃO PASSADOS POR MEIO DE UM DICIONARIO DE VALORES E CHAVES -->
    <!-- <div
      v-for="(obj, index) in todos"
      :key="obj.id"
      class="todos-item"
    >
      <img
        v-if="obj.imgSrc"
        :src="obj.imgSrc"
      >
      {{index }} - {{ obj.title }}
    </div> -->

    <!-- Caixa de Texto -->
    <!-- <br><br>
    <div>
      <input
        v-model="name"
        type="text"
        
      >
      <br>
    </div>
    {{ name }} -->

    <!-- Caixa de Seleção de opçoes -->
    <!-- <div>
      <br>
      <label>Sports</label>
      <br>
      <select v-model="sports">
        <option value="">Escolha</option>
        <option value="futebol">Futebol</option>
        <option value="skate">Skate</option>
        <option value="basquete">Basquete</option>
      </select>
    </div>
    {{ sports }} -->


    <!-- Caixa de opções booleanas -->
    <!-- <br><br>
    <div>
      <label>fodase</label>
      <input 
      v-model="newsletter"
      type="radio"
      value="Sim"
      >Sim
    
      <input 
      v-model="newsletter"
      type="radio"
      value="Não">Não
    </div>
    {{ newsletter }} -->


    <!-- Caixa de Confirmação booleana -->
    <!-- <br><br>
    <div>
      <label>Contrato</label>
      <input 
      v-model="contrato"
      type="checkbox"
      
      >termos do sex
    </div>

    <br><br> -->

    <!-- Array de opções -->
    <!-- <div>
      <label>Colors</label>
      <input
      v-model="colors"
      type="checkbox"
      value="azul"
      >azul
      <input
      v-model="colors"
      type="checkbox"
      value="red"
      >red
    </div> -->
    <br><br>
    <div>
      <button @click.stop="submit()"> Enviar</button>

      <div 
        @mouseover.once="onMouseOver()"
        @mouseout.once="onMouseOut()"
      >
        asdsa
      </div>

    </div>
    
    <br><br>

    <div>
      <form action="https://google.com" 
      @click.prevent="onSubmit()"
      >
        <button type="submit">Enviar</button>
      </form>
    </div>

  </div>
 

</template>

<script>
import MyHeader from './components/MyHeader.vue'

export default {
  name: 'App',
  components: {
    MyHeader
  },
  // local para criar variáveis
  data() {
    return {
      colors:[],
      contrato:'',
      newsletter:'',
      sports:'skate',
      name:'teste',
      isHome: false,
      showHeader: true,
      showName: true,
      firstName: 'jon',
      lastName: 'snow',
      acessLevel: 'admin',
      todos: [  
                {
                  "userId": 1,
                  "id": 1,
                  "title": "delectus aut autem",
                  "completed": false,
                  "imgSrc":"https://fakeimg.pl/150x150"

                },
                {
                  "userId": 1,
                  "id": 2,
                  "title": "quis ut nam facilis et officia qui",
                  "completed": false
                },
                {
                  "userId": 1,
                  "id": 3,
                  "title": "fugiat veniam minus",
                  "completed": false
                },
                {
                  "userId": 1,
                  "id": 4,
                  "title": "et porro tempora",
                  "completed": true
                },
                {
                  "userId": 1,
                  "id": 5,
                  "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
                  "completed": false,
                  "imgSrc":"https://fakeimg.pl/150x150"
                }
              ]  
    }
  },
  // local para criar funções
  methods: {
    submit(){
      console.log('submit')
    },
    onMouseOver(){
      console.log('mouse over')
    },
    onMouseOut(){
      console.log('mouse out')
    },
    onSubmit(){
      console.log('submitt')
    }
  }
}
</script>

<style>
.title{ 
  font-size: 20px;
  color:blue;
}
.title-home{
  font-size: 40px;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  color: green;
}
.text{
  color: blueviolet;
}
.todos-item{
  background: #000;
  color: #fff;
  margin: 0 0 5px 0;
  padding: 3px;

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
