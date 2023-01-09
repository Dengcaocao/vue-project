<template>
  <div class="main">
    <Layout class="layout">
      <div class="canvas"></div>
      <ActionBar />
      <div class="btn-group">
        <button class="btn-item">随机生成</button>
        <button class="btn-item">下载头像</button>
        <button class="btn-item">批量生成</button>
      </div>
    </Layout>
    <Sider />
  </div>
</template>
<script setup lang="ts">
import Layout from './layout/index.vue'
import Sider from './layout/sider.vue'
import ActionBar from './components/ActionBar.vue';
</script>
<style scoped lang="scss">
@import './styles/var.scss';
.main {
  display: flex;
  min-height: 100vh;
  background-color: $color-page-bg;
  background-image: radial-gradient(
    rgba($color-secondary, 0.8) 20%,
    rgba($color-secondary, 0.6) 40%,
    rgba($color-secondary, 0.4) 60%,
    rgba($color-secondary, 0.2) 80%,
    transparent 100%
  );
  .layout {
    flex: 1;
    .canvas {
      width: 240px;
      height: 240px;
      border-radius: 8px;
      margin: 100px auto 80px auto;
      background-image: linear-gradient(90deg, #ffecd2, #fcb69f);
    }
    .btn-group {
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 80px auto;
      .btn-item {
        border: none;
        outline: none;
        color: $color-text;
        padding: 10px 20px;
        margin: 0 10px;
        border-radius: 8px;
        font-weight: bold;
        cursor: pointer;
        background-color: $color-gray;
        &:hover {
          color: lighten($color-text, 10);
        }
      }
    }
  }
}
</style>

