<template>
  <section class="sider">
    <button class="collapsed">
      <img :src="Right" width="100%" alt="right">
    </button>
    <SectionWarp title="画布大小">
      <div class="item-warp">
        <button class="item">120x120</button>
        <button class="item">240x240</button>
      </div>
    </SectionWarp>
    <SectionWarp title="字体">
      <div class="item-warp">
        <button class="item">120x120</button>
        <button class="item">240x240</button>
      </div>
    </SectionWarp>
    <SectionWarp title="颜色">
      <div class="item-warp">
        <input type="color" v-model="config.color">
      </div>
    </SectionWarp>
  </section>
</template>
<script setup lang="ts">
import { reactive, watch } from 'vue'
import Right from '@/components/icons/icon-right.svg'
import SectionWarp from '@/components/SectionWarp.vue'
const emit = defineEmits(['getConfig'])
const config = reactive({
  size: '',
  family: '',
  color: '#D62E2E'
})
watch(config, newConfig => {
  emit('getConfig', newConfig)
})
</script>
<style scoped lang="scss">
@import '../styles/var.scss';
.sider {
  position: relative;
  top: 0;
  right: 0;
  bottom: 0;
  width: 360px;
  padding: 30px 20px;
  background-color: skyblue;
  .collapsed {
    position: absolute;
    top: 50%;
    left: 0;
    width: 20px;
    height: 40px;
    background-color: $color-configurator;
    transform: translate(-100%, -50%);
    border: none;
    padding: 0;
    cursor: pointer;
    border-radius: 4px 0 0 4px;
    &:focus {
      // outline-style: groove;
      // outline-width: 2px;
      // outline-color: $color-text;
    }
    img {
      display: block;
      width: 100%;
      height: 100%;
    }
  }
  .item-warp {
    display: flex;
    flex-wrap: wrap;
    .item {
      margin-right: 8px;
    }
  }
}
</style>