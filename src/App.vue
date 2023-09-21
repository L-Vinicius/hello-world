<template>
  <div> 
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
    
      <div
        v-for="(obj, index) in todos"
        :key="obj.id"
        class="todos-item"
      >
        <img
          v-if="obj.imgSrc"
          :src="obj.imgSrc"
        >
        {{index }} - {{ obj.title }}
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
  data() {
    return {
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
  }
}
</script>

<style>
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
