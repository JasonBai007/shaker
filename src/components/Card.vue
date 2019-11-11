<template>
  <div class="card-wrap">
    <img src="../assets/img/setting.png" alt />
    <div class="right">
      <span>川普总统</span>
      <img src="../assets/img/man.png" alt />
      <!-- <img src="../assets/img/woman.png" alt /> -->
      <p>翻脸比翻书快</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "card"
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