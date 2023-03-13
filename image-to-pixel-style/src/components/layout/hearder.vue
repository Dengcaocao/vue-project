<template>
  <header class="hearder">
    <div class="logo-warp">
      <h2>Pixel Image</h2>
    </div>
    <a class="store" href="" target="_blank">
      <img src="@/assets/github-fill.svg" alt="">
      <span>Github</span>
    </a>
  </header>
</template>
<script setup lang="ts">

</script>
<style scoped lang="scss">
.hearder {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 30px;
  height: 88px;
  // background-color: #0e1116;
  .logo-warp {
    h2 {
      color: #fff;
      font-weight: bolder;
    }
  }
  .store {
    overflow: hidden;
    display: block;
    line-height: 30px;
    color: #fff;
    padding: 2px 10px;
    border-radius: 4px;
    background-color: #41474d;
    img {
      width: 26px;
      vertical-align: middle;
      filter: drop-shadow(#fff 100px 0);
      transform: translateX(-100px);
    }
    span {
      margin: 4px;
      vertical-align: middle;
      font-size: 18px;
      font-weight: bold;
    }
  }
}
</style>
