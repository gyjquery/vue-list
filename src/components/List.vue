<template>
   <ul>
     <Item v-for="(todo,index) in todos" :key="index" :todo="todo" :index="index"/>
   </ul>
</template>

<script>
  import Item from "./Item.vue"
  export default {
    props:{
      todos:Array
    },
     components:{
       Item
     }
  }
</script>

<style>
   ul{
     list-style: none;
   }
</style>
