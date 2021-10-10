<template>
<div>
    <h2>购物车</h2>
    <div class="all-box">
      <div @click="login" >登录</div>
    </div>
</div>
</template>

<script>
export default {
  name: 'Cart',
  methods:{
    login(){
     this.$router.push('login')
    }
  }
}
</script>

<style scoped>
.all-box{
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
