<template>
  <div class="card-wrap animated fadeInDown" v-show="isShow">
    <img :src="obj.url" />
    <div class="right">
      <span>{{obj.name}}</span>
      <img v-if="obj.sex" src="../assets/img/man.png" />
      <img v-else src="../assets/img/woman.png" />
      <p>{{obj.desc}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
  data() {
    return {
      isShow: false,
      obj: {
        name: "",
        sex: 1,
        url: "",
        desc: ""
      }
    };
  },
  mounted() {
    this.$bus.$on("getOne", data => {
      this.showCard(data);
    });
    this.$bus.$on("clear", () => {
      this.hideCard();
    });
  },
  methods: {
    showCard(data) {
      this.obj = data;
      this.isShow = true;
    },
    hideCard() {
      this.obj = {
        name: "",
        sex: 1,
        url: "",
        desc: ""
      };
      this.isShow = false;
    }
  }
};
</script>

<style lang="less">
.card-wrap {
  position: absolute;
  bottom: 12vh;
  z-index: 2;
  background: #4d4e58;
  width: 86vw;
  left: 7vw;
  border-radius: 5px;
  display: flex;
  padding: 2vw;
  box-sizing: border-box;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
  & > img {
    width: 14vw;
    height: 14vw;
    border-radius: 5px;
  }
  .right {
    flex-grow: 1;
    text-align: left;
    margin-left: 3vw;
    padding-top: 9px;
    img {
      width: 4.5vw;
      display: inline-block;
      margin-left: 8px;
      vertical-align: bottom;
    }
    p {
      margin-top: 5px;
    }
  }
}
</style>