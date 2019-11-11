<template>
  <div class="card-wrap animated fadeInDown" v-if="isShow">
    <img src="../assets/img/setting.png" alt />
    <div class="right">
      <span>{{obj.name}}</span>
      <img v-if="obj.sex" src="../assets/img/man.png" alt />
      <img v-else src="../assets/img/woman.png" alt />
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
  bottom: 16vh;
  z-index: 2;
  background: #4d4e58;
  width: 86vw;
  left: 7vw;
  border-radius: 5px;
  display: flex;
  padding: 2vw;
  box-sizing: border-box;
  & > img {
    width: 14vw;
  }
  .right {
    flex-grow: 1;
    text-align: left;
    margin-left: 2.5vw;
    padding-top: 9px;
    img {
      width: 4vw;
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