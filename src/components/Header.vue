<template>
   <div class="header">
      <input type="text" placeholder="请输入信息" v-model="content" @keyup.enter="addTodo"/>
   </div>
</template>

<script>
  export default {
    data () {
      return {
          content:""
      }
    },
    methods: {
      addTodo(){
        const content = this.content.trim()
        if(!content){
           return
        }
        this.$emit("addContent",content)
         this.content=""
      }
    }

  }
</script>

<style scoped>
   .header input{
     width:600px;
     height:50px;
     -webkit-border-radius: 2px;
     -moz-border-radius: 2px;
     border-radius: 2px;
     border:1px solid #ccc;
     padding: 0 20px;
     box-sizing: border-box;
   }
</style>
