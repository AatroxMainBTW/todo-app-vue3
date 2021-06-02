<template>
  <div class="container">
    <form @submit.prevent="addTodo">
      <div class="space-y-2">
        <div class="">
          <label for="todo_title" class="text-white mr-2">Title</label>
          <input type="text" name="todo_title" v-model="todo.title"/>
        </div>
        <br />
        <div class="mt-2 mr-16">
          <label for="todo_description" class="text-white mr-2">Description</label>
          <input type="text" name="todo_description" v-model="todo.description" />
        </div>
        <br />
        <div class="mt-2">
          <label for="todo_tag" class="text-white mr-2">Tag</label>
          <input type="text" name="todo_tag" v-model="todo.tag" />
        </div>
        <br />
        <div class="">

        </div>
        <div class="">

        </div>
        <div class="">

        </div>
        <button
        type="submit"
        class="bg-red-700 text-xs text-white py-2 px-2 rounded-lg hover:bg-red-500 transition duration-500 focus:outline-none"
        >
        Add todo
        </button>
      </div>
    </form>
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
