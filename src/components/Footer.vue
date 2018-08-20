<template>
  <footer>
    <div><input type="checkbox" value="allCheck" v-model="allCheck"/><span>全选/全不选</span></div>
    <div><span>已完成{{complete}}</span>/<span>全部{{todos.length}}</span></div>
    <div><a href="javascript:;" @click="delComplete">删除已完成</a></div>
  </footer>
</template>

<script>
  export default {
    data(){
      return{

      }
    },
    props:{
      todos:Array
    },
    computed:{
      complete(){
        return this.todos.reduce((pre,todo)=>(pre+(todo.checked?1:0))
        ,0)
      },
      allCheck:{
         get(){
         return this.todos.reduce((pre,todo)=>(pre+(todo.checked?1:0)),0) === this.todos.length
        },
        set(value){
          this.$emit("allCheck",value)
          console.log(value)
        }
      }

    },
    methods:{
      delComplete(){
         const todos = this.todos.filter((todo,index)=>(!todo.checked))
         this.$emit('delComplete',todos)
      }
    }
  }
</script>

<style>
 footer{
  display: flex;
   justify-content: space-between;
   align-items: center;
   width:600px;
 }
 a{
   text-decoration: none;
   color: #fff;
   background: red;
   font-size: 20px;
   border-radius: 5px;
   padding:5px;
   box-sizing: border-box;
   display: block;
 }

</style>
