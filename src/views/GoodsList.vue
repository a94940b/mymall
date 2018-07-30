<template>
 <div>
   这是商品列表页面
   <!-- /goods页面下面有子路由，所有这里要定义router-view -->
   <router-link to="/goods/title">显示商品标题</router-link>
   <router-link to="/goods/image">显示商品图片</router-link>
   <div>
     <router-view></router-view>
   </div>
   <router-link to="/cart">跳转到购物车页面</router-link>
   <button @click="jump">button跳转到购物车页面</button>
 </div>
</template>

<script>
export default {
  // push里面可以直接传入字符串url进行跳转
  // this.$router.push('/cart')
  // 也可以传入对象
  // url可以传入参数
  methods: {
    jump () {
      this.$router.push({path: '/cart?goodsId=123'});
    }
  }
}
</script>

<style>

</style>
