<template lang="html">
    <div id="card" class="bg-gray-500 bg-opacity-20 rounded-xl w-96 px-2 py-2 mt-5">
      <div id="card-title" class="text-white text-left ml-2">
        <span>{{title}}</span>
      </div>
      <hr class="opacity-50" />
      <div id="card-description" class="text-white text-xs text-left ml-5 mt-3">
        <span>{{description}}</span>
      </div>
        <div id="card-tag" class="text-white text-xs mt-3 bg-gray-500 rounded-full px-2 py-2 w-20">
            <span>{{tag}}</span>
        </div>
        <button
        @click="del"
        class="bg-red-700 text-xs text-white py-2 px-2 rounded-lg hover:bg-red-500 transition duration-500 focus:outline-none"
        >
        Delete
        </button>
    </div>

</template>

<script>
  export default {
    props:[
      'id',
      'title',
      'description',
      'tag'
    ],
    setup(props,ctx){
      const del = function(){
        ctx.emit('del')

      }
      return{
        del
      }
    }
  }
</script>

<style lang="css">
</style>
