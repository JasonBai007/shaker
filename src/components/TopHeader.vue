<template>
  <div class="header-wrap">
    <span>抖一抖</span>
    <img src="../assets/img/setting.png" alt />
  </div>
</template>

<script>
export default {
  name: "TopHeader"
};
</script>

<style lang="less">
.header-wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 20px;
  padding: 4vw;
  img {
    width: 26px;
  }
}
</style>