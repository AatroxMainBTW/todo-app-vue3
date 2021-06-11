
<template>
  <div class="container">
   
    
        <div class="">
          <label for="todo_title" class="text-white mr-2">Title</label>
          <input type="text" name="todo_title" v-model="todo.title"/>
        </div>
        <div class="">
          <label for="todo_description" class="text-white mr-2">Description</label>
          <input type="text" name="todo_description" v-model="todo.description" />
        </div>
        <div class="">
          <label for="todo_tag">Tag</label>
          <input type="text" name="todo_tag" v-model="todo.tag" />
        </div>
       
       <div>
         <form @submit.prevent="addTodo">
        <button
        type="submit"
        class="addBtnstyle"
        >
        Add todo
        </button>
      
    </form>
       </div>
      
    
  </div>
</template>

<script>
import {ref} from "vue";

export default {
  setup(props, ctx){
    let todo = ref({
      id:0,
      title:"",
      description:"",
      tag:"",
      color:""
    })
    const addTodo = function(){
      todo.value.id = Date.now()
      console.log("addtodo-from Form.vue",todo.value);
      ctx.emit("add",todo.value);
    }

    return {
      todo,
      addTodo
    }
  }
}
</script>

<style lang="scss">

</style>