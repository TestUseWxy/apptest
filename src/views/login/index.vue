<template>
  <div>
    <h1>我是登录页</h1>
    <input v-model="phone">
    <br>
    <input v-model="password">
    <div @click="logins">
      登录
    </div>
  </div>
</template>

<script>
import data from './test.js'
export default {
   data () {
    return {
      phone:'',
      password:'',
      msg:""
    }
  },
  mounted(){
    console.log(data);
  },
  methods:{
    logins(){
      localStorage.setItem('phone','15761689887')
      localStorage.getItem('phone')
      sessionStorage.setItem('call','44455545')
      sessionStorage.getItem('call')
      console.log(this.phone);
      this.msg='qweqweqw'
      console.log(this.password);
      // if(this.phone!='15761698107'&&this.password!='123'){
      //  alert('登录失败')
      // }else{
      //   this.$router.replace('home')
      // }
    }
  }
}
</script>

<style>

</style>