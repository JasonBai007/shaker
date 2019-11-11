<template>
  <div class="wrap">
    <div class="splits">
      <div :class="[isOpen? 'open': '', 'inner1']" @click="open"></div>
      <div :class="[isOpen? 'open': '', 'inner2']"></div>
    </div>
    <img src="../assets/img/bg.jpg" id="bg-img" />
  </div>
</template>

<script>
export default {
  name: "middle",
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    open() {
      this.isOpen = true;
    }
  }
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
    z-index: 1;
    overflow: hidden;
    & > div {
      height: 50%;
      transition: all 0.3s ease-out;
    }
    .inner1 {
      background: url("../assets/img/yao.png") no-repeat 50% 200% #323340;
      &.open {
        transform: translateY(-14vh)
      }
    }
    .inner2 {
      background: url("../assets/img/yao.png") no-repeat 50% -110% #323340;
      &.open {
        transform: translateY(14vh)
      }
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