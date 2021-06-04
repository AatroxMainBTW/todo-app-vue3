<template>
  <div class="">
    <Form @add="saveTodo" />
    <div v-for="todo in todos" v-bind:key="todo.id" class="space-y-2 ml-80">
      <div id="card" class="bg-gray-500 bg-opacity-20 rounded-xl w-96 px-2 py-2 mt-5">
        <div id="card-title" class="text-white text-left ml-2">
          <span>{{todo.title}}</span>
        </div>
        <hr class="opacity-50" />
        <div id="card-description" class="text-white text-xs text-left ml-5 mt-3">
          <span>{{todo.description}}</span>
        </div>
          <div id="card-tag" class="text-white text-xs mt-3 bg-gray-500 rounded-full px-2 py-2 w-20">
              <span>{{todo.tag}}</span>
          </div>
          <button
          class="bg-red-700 text-xs text-white py-2 px-2 rounded-lg hover:bg-red-500 transition duration-500 focus:outline-none"
          @click="deletetodo(todo)"
          >
          Delete
          </button>
      </div>
    </div>
  </div>


</template>

<script>
import Form from './components/Form.vue';
//import card from './components/card.vue';

import {ref} from "vue";

export default {
  name: 'App',
  components: {
    Form,
    //card
  },
  setup(){
    let todos = ref([]);
    //let newtodos = ref([])
    const saveTodo = function(data){
      console.log("saveTodo-from App.vue", data)
      todos.value = [...todos.value, {title: data.title, id:data.id, description:data.description, tag:data.tag}]
    }
    const deletetodo = function(data){
      //console.log("ssss",data)
      var index = todos.value.indexOf(data);
      console.log(index);
      todos.value.splice(index)

    }
    return{
      saveTodo,
      deletetodo,
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
