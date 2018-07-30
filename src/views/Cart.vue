<template>
 <div>
  这是购物车页面
  <!-- 获取一下我们url地址里面的参数
  通过 $route.query.参数名 拿到参数对应的值 -->
  <span>{{$route.query.goodsId}}</span>
 </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
