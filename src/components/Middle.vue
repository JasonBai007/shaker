<template>
  <div class="wrap">
    <div class="splits">
      <div class="inner1"></div>
      <div class="inner2"></div>
    </div>
    <img src="../assets/img/bg.jpg" id="bg-img" />
  </div>
</template>

<script>
export default {
  name: "middle"
};
</script>

<style lang="less">
.wrap {
  height: 80vh;
  background: #292c31;
  position: relative;
  .splits {
    position: absolute;
    width: 100%;
    height: 100%;
    background: red;
    z-index: 1;
    & > div {
      height: 50%;
      background: green;
    }
  }
  #bg-img {
    width: 26vw;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}
</style>