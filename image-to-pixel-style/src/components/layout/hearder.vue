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
  .logo-warp {
    h2 {
      font-weight: bolder;
    }
  }
  .store {
    display: block;
    line-height: 30px;
    color: var(--color-text);
    img {
      width: 30px;
      vertical-align: middle;
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
