<template>
  <div id="app">
    <top-header></top-header>
    <middle></middle>
    <card></card>
  </div>
</template>

<script>
import TopHeader from "./components/TopHeader";
import Middle from "./components/Middle";
import Card from "./components/Card";

export default {
  name: "app",
  components: {
    TopHeader,
    Middle,
    Card
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
