<template>
  <li>
    <input type="checkbox" v-model="todo.checked"/>
    <span>{{todo.text}}</span>
    <span class="delete" @click="del"><a href="javascript:;">删除</a></span></li>
</template>

<script>
 import PubSub from 'pubsub-js'
  export default {
    data () {
      return {

      }
    },
     props:{
      todo:Object,
       index:Number
     },
    methods: {
      del(){
        PubSub.publish("index",this.index)
      }
    },
    watch:{

    }
  }
</script>

<style scoped>
 li{
   height:50px;
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

  }
  .delete{
    visibility: hidden;
  }
 li:hover .delete{
   visibility: visible;
  }
</style>
