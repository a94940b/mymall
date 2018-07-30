<template>
 <div>
   这是商品列表页面
   <!-- /goods页面下面有子路由，所有这里要定义router-view -->
   <router-link to="/goods/title">显示商品标题</router-link>
   <router-link to="/goods/image">显示商品图片</router-link>
   <div>
     <router-view></router-view>
   </div>
 </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
