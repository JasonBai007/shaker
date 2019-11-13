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
      isOpen: false,
      last_update: 0,
      x: 0,
      y: 0,
      z: 0
    };
  },
  mounted() {
    //运动事件监听
    if (window.DeviceMotionEvent) {
      window.addEventListener("devicemotion", this.deviceMotionHandler);
    }
  },
  methods: {
    deviceMotionHandler(eventData) {
      let curTime = new Date().getTime();
      let diffTime = curTime - this.last_update;
      // 每隔1s判断一下
      if (diffTime > 1000) {
        this.last_update = curTime;
        // 获取重力加速度对象
        let acceleration = eventData.accelerationIncludingGravity;
        // 拿到三个方向上的重力加速度的正整数部分，摇动的时候会超过10
        this.x = Math.floor(Math.abs(acceleration.x));
        this.y = Math.floor(Math.abs(acceleration.y));
        this.z = Math.floor(Math.abs(acceleration.z));
        // 摇晃幅度如果特别大，就open
        if (this.x > 10 || this.y > 10 || this.z > 10) {
          this.open();
        }
      }
    },
    open() {
      // 振动300ms
      if (navigator.vibrate) {
        navigator.vibrate(300);
      } else if (navigator.webkitVibrate) {
        navigator.webkitVibrate(300);
      }
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
  height: 65vh;
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
      background: url(../assets/img/yao.png) no-repeat 27vw 16vh #323340;
      background-size: 45%;
      &.open {
        animation: moveA 1s;
      }
    }
    .inner2 {
      background: url(../assets/img/yao.png) no-repeat 27vw -16.5vh #323340;
      background-size: 45%;
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

// 兼容iphone6，iphone7，iphone8s
@media (device-height: 667px) and (-webkit-min-device-pixel-ratio: 2) {
  .wrap {
    height: 70vh;
  }
  .wrap .splits .inner1 {
    background: url(../assets/img/yao.png) no-repeat 24vw 20vh #323340;
  }
  .wrap .splits .inner2 {
    background: url(../assets/img/yao.png) no-repeat 24vw -15vh #323340;
  }
}

// 兼容iphone6 Plus,iphone7 Plus,iphone8 Plus：
@media (device-height: 736px) and (-webkit-min-device-pixel-ratio: 2) {
  .wrap {
    height: 70vh;
  }
  .wrap .splits .inner1 {
    background: url(../assets/img/yao.png) no-repeat 24vw 20vh #323340;
  }
  .wrap .splits .inner2 {
    background: url(../assets/img/yao.png) no-repeat 24vw -15vh #323340;
  }
}

// 兼容iphoneX
@media only screen and (device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) {
  .wrap {
    height: 70vh;
  }
  .wrap .splits .inner1 {
    background: url(../assets/img/yao.png) no-repeat 24vw 22vh #323340;
  }
  .wrap .splits .inner2 {
    background: url(../assets/img/yao.png) no-repeat 24vw -13vh #323340;
  }
}
</style>