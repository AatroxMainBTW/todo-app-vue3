<template>
  <Form @add="saveTodo" />
  <ul>
    <li v-for="todo in todos" v-bind:key="todo.id">{{todo.title}}</li>
  </ul>
</template>

<script>
import Form from './components/Form.vue'
import {ref} from "vue";

export default {
  name: 'App',
  components: {
    Form
  },
  setup(){
    let todos = ref([]);
    const saveTodo = function(data){
      console.log("saveTodo-from App.vue", data)
      todos.value = [...todos.value, {title: data.title, id:data.id, description:data.description}]
    }
    return{
      saveTodo,
      todos
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
