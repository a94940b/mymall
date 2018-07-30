<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view class="main"></router-view>
    命名视图，可以实现根页面加载出来三个不同的组件，实现布局效果
    <router-view name="title" class="left"></router-view>
    <router-view name="image" class="right"></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  font-size: 30px;
}
.left,
.right {
  float: left;
  width: 49%;
  border: 1px solid #eee;
}
</style>
