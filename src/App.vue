<template>
  <div id="card-container" class="card-container">
    <Form @add="saveTodo" />
    <div v-for="todo in todos" v-bind:key="todo.id" class="space-y-2 ml-80">
      <div id="card" class="card">
        <div id="card-title" class="card-title">
          <span>{{todo.title}}</span>
        </div>
        <div class="hr1">
          <hr  />
        </div>
        <div id="card-description" class="card-description">
          <span>{{todo.description}}</span>
        </div>
          <div id="card-tag" class="card-tag">
              <span>{{todo.tag}}</span>
          </div>
          <button
          class="deleteBtnStyle"
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
