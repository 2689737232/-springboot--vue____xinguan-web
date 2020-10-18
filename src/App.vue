<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  created() {
    if (!this.$route.fullPath == "/login") {
      // 打开默认导航到登录页面
      this.$router.push("login");
    }
  },
};
</script>

<style lang="less">
#app {
  overflow: hidden;
}
</style>
