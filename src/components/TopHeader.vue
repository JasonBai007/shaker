<template>
  <div class="header-wrap">
    <span class="animated wobble">抖一抖</span>
    <img class="animated swing" src="../assets/img/setting.png" alt @click="gotoGithub" />
  </div>
</template>

<script>
export default {
  name: "TopHeader",
  methods: {
    gotoGithub() {
      window.open("https://github.com/JasonBai007/shaker");
    }
  }
};
</script>

<style lang="less">
.header-wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
  padding: 4vw;
  img {
    width: 24px;
  }
}
</style>