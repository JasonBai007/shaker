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
      setTimeout(() => {
        this.isOpen = false;
        this.$bus.$emit("getOne", {
          name: "白总",
          sex: 1,
          desc: "白总辛苦了"
        });
      }, 1000);
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
    }
    .inner1 {
      background: url("../assets/img/yao.png") no-repeat 50% 200% #323340;
      &.open {
        animation: moveA 1s;
      }
    }
    .inner2 {
      background: url("../assets/img/yao.png") no-repeat 50% -110% #323340;
      &.open {
        animation: moveB 1s;
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

@keyframes moveA {
  0% {
    transform: translateY(0vh);
  }
  50% {
    transform: translateY(-14vh);
  }
  100% {
    transform: translateY(0vh);
  }
}
@keyframes moveB {
  0% {
    transform: translateY(0vh);
  }
  50% {
    transform: translateY(14vh);
  }
  100% {
    transform: translateY(0vh);
  }
}
</style>