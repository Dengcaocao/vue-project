<template>
  <div class="action">
    <div class="action-item">
      <img :src="Next">
    </div>
    <div class="action-item">
      <img :src="Back">
    </div>
    <div class="action-item">
      <img :src="Flip">
    </div>
  </div>
</template>
<script setup lang="ts">
import Flip from '@/components/icons/icon-flip.svg'
import Back from '@/components/icons/icon-back.svg'
import Next from '@/components/icons/icon-next.svg'
</script>
<style scoped lang="scss">
@import '@/styles/var.scss';
.action {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 200px;
  margin: 0 auto;
  padding: 8px 12px;
  border-radius: 40px;
  background-color: $color-gray;
  .action-item {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    cursor: pointer;
    background-color: lighten($color-gray, 10);
  }
}
</style>