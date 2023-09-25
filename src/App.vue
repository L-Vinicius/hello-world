<template>
  <div> 

    <!-- <h1 :class= "{'title':true, 'title-home':isHome}">
      CURSO 3D
    </h1> -->

    <!-- <p :class="['text','title']">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum fuga modi provident iusto! Temporibus obcaecati accusamus earum blanditiis reprehenderit quos explicabo quisquam necessitatibus, tempora sequi, fugit, quam possimus praesentium cumque.
    </p> -->

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
    <!-- <div v-show="showName">
        Nome: {{user.firstName}} <br>
        Sobrenome: {{ user.lastName }} 
    </div> -->
    <!-- ------------------------------------------------ -->

    <!-- CRIA UMA LISTA DE VALORES ATRAVÉS DO v-for, ONDE OS VALORES SÃO PASSADOS POR MEIO DE UM DICIONARIO DE VALORES E CHAVES -->
    <h2>Todos em aberto</h2>
    <div
      v-for="(obj, index) in uncompletedTodos"
      :key="obj.id"
      class="todos-item"
    >
      <img
        v-if="obj.imgSrc"
        :src="obj.imgSrc"
      >
      {{index }} - {{ obj.title }}
    </div>

    <h2>Todos completas</h2>
    <div
      v-for="(obj, index) in completedTodos"
      :key="obj.id"
      class="todos-item"
    >
      {{index }} - {{ obj.title }}
    </div>

    <br><br>
    <h2>todos</h2>
    <div
    v-for="obj in todos"
    :key="obj.id"
    class="todos-items"
    >
      <input
        v-model="obj.completed"
        type="checkbox"
      >
      {{ obj.title }}
    </div>



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
    <!-- <br><br>
    <div>
      <button @click="onClick"> enviar</button>
      
      <div 
        @mouseover.once="onMouseOver()"
        @mouseout.once="onMouseOut()"
      >
      onclick
      </div>

    </div> -->
    
    <!-- <br><br>

    <div>
      <form action="https://google.com" 
      @click.prevent="onSubmit()"
      >

      
      <input
      type="text"
      @keypress.space.enter="onKeyPress"
      >
      <button type="submit">submit</button>
      
      </form>
    </div> -->


  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'

export default {
  name: 'App',
  components: {
    MyHeader
  },
  // (data): local para criar variáveis
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
      acessLevel: 'admin',
      todos: [  
        {
          "userId": 1,
          "id": 1,
                  "title": "delectus aut autem",
                  "completed": false,

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
          "completed": true
        },
        {
          "userId": 1,
          "id": 4,
          "title": "et porro tempora",
          "completed": true
        },
        // {
        //   "userId": 1,
        //   "id": 5,
        //   "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
        //   "completed": false,
        //   "imgSrc":"https://fakeimg.pl/150x150"
        // }
              ], 
      user: {
        firstName: 'jon',
        lastName: 'snow',
      }
    }
  },
  // (computed): local para declarar funções que serão tratadas como campo normal, PRECISA UTILIZAR O return na função, depende do valor de outras variáveis
  computed: {
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`
    },
    uncompletedTodos(){
      return this.todos.filter(todo => !todo.completed)
    },
    completedTodos(){
      return this.todos.filter(todo => todo.completed)
    },
  },
  // (methods) : local para criar funções
  methods: {
    // a primeira variável sempre será a que mostra o evento da função
    onClick($evt){
      console.log('click',$evt,this.user)
    },
    onMouseOver(){
      console.log('mouse over')
    },
    onMouseOut(){
      console.log('mouse out')
    },
    onSubmit(){
      console.log('submitt')
    },
    onKeyPress($evt){
      console.log($evt)
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
  align-items: left;
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
