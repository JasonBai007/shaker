<template>
  <div class="wrap">
    <div class="splits">
      <div :class="[isOpen? 'open': '', 'inner1']" @click="open"></div>
      <div :class="[isOpen? 'open': '', 'inner2']" @click="open"></div>
    </div>
    <img src="../assets/img/bg.jpg" id="bg-img" />
  </div>
</template>

<script>
import people from "@/assets/json/info.js";
export default {
  name: "middle",
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    open() {
      // 先清除掉上次摇到的人
      this.$bus.$emit("clear");
      // 裂开
      this.isOpen = true;
      // 合上后，清除class中的open，然后释放一个事件
      this.sendInfo();
    },
    sendInfo() {
      setTimeout(() => {
        this.isOpen = false;
        let i = Math.floor(Math.random() * people.length);
        this.$bus.$emit("getOne", people[i]);
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
      background: url(/img/yao.54c609ee.png) no-repeat 26vw 26vh #323340;
      &.open {
        animation: moveA 1s;
      }
    }
    .inner2 {
      background: url("../assets/img/yao.png") no-repeat 26vw -14vh #323340;
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