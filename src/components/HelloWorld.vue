<template>
<div>
<span>{{message}}</span><br>
<span>{{reverseMessage}}</span>
</div>
</template>

<script>
export default {
  data(){
    return {
      message:"hello word",
      login:false,
      todos:[
        {name:"韩",sex:"男"},
         {name:"振",sex:"男"},
          {name:"方",sex:"男"},
      ]
  }
  },
  methods:     {
    handleReverse(){
      this.message = this.message.split(" ").reverse().join(" ");
    },
    handleLogin(){
      this.login=!this.login;
    },
    doSomething(){
      console.log(this)
    }
  },
  computed:{
  reverseMessage(){
  return this.message.split(" ").reverse().join(" ");
  }
  },
  mounted(){
  console.log(this.reverseMessage)
  }
}
</script>


