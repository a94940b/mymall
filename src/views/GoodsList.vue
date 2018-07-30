<template>
 <div>
   这是商品列表页面
   <!-- 命名路由，用v-bind:to="{name:'路由名'}"，并且还带参数 。 这里的params指的是路由的参数，不是页面跳转的参数 -->
   <router-link :to="{name:'cart',params:{cartId:123}}">跳转到购物车页面</router-link>
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
