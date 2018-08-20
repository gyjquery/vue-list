<template>
  <div class="main">
    <Header @addContent="addContent"/>
    <List :todos="todos"/>
    <Footer @allCheck="allCheck" :todos="todos" @delComplete="delComplete"/>
  </div>
</template>

<script>
   import Header from './components/Header.vue'
   import List from './components/List.vue'
   import Footer from './components/Footer.vue'
   import PubSub from 'pubsub-js'
  export default {

  name: 'App',
  data(){
    return{
      todos:[
        {text:"12123",checked:true}
        ],
      b:false
    }
  },
  methods:{
    addContent(todo){
      this.todos.push({text:todo,checked:false})
    },
    allCheck(isCheck){
//      console.log(isCheck)
       this.todos.forEach((todo,indexs)=>{
          todo.checked=isCheck
       })
    },
    delComplete(del){
         this.todos=del
    }
  },
    mounted(){
          PubSub.subscribe("index",(msg,index)=>{
             this.todos.splice(index,1)

          })

    },
    watch:{

    },
    components:{
      Header,
      List,
      Footer
    }

}
</script>

<style scoped>
 .main{
   width:800px;
   margin: 10px auto;
 }
</style>
