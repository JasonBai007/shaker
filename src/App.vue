<template>
  <div id="app">
    <top-header></top-header>
    <middle></middle>
  </div>
</template>

<script>
import TopHeader from "./components/TopHeader.vue";
import Middle from "./components/Middle.vue";

export default {
  name: "app",
  components: {
    TopHeader,
    Middle
  }
};
</script>

<style lang="less">
body {
  background: #323340;
}
#app {
  font-family: "Microsoft YaHei", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
}
</style>
