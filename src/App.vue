<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
import "./mockjs/mock-data.js";

export default {
  created() {
    if (this.$route.fullPath != "/Home") {
      console.log(this.$route.fullPath);
      // 打开默认导航到登录页面
      this.$router.push("Home");
    }
  },
};


</script>

<style lang="less">

</style>
