<template>
  <div class="main">
    <Layout class="layout">
      <div class="layout-content">
        <canvas
          width="240"
          height="240"
          ref="canvas"
          class="canvas"
          @mousedown="drawStart"
          @mousemove="move"
          @mouseup="drawEnd"
          @mouseleave="drawEnd"></canvas>
        <ActionBar />
        <div class="btn-group">
          <button class="btn-item">随机生成</button>
          <button class="btn-item">下载头像</button>
          <button class="btn-item">批量生成</button>
        </div>
      </div>
    </Layout>
    <Sider @getConfig="setConfig" />
  </div>
</template>
<script setup lang="ts">
import { ref, reactive, onMounted } from 'vue'
import Layout from './layout/index.vue'
import Sider from './layout/sider.vue'
import ActionBar from './components/ActionBar.vue'

const canvas: any = ref(null)
const ctx: any = ref(null)
let isStart = ref(false)
let x = ref(0)
let y = ref(0)

let config: Object = reactive({
  color: ''
})

function drawStart (e: MouseEvent) {
  console.log(e)
  ctx.value.beginPath()
  isStart.value = true
  x.value = e.offsetX
  y.value = e.offsetY
}

function move (e: MouseEvent) {
  if (!isStart.value) return
  ctx.value.lineWidth = 5
  ctx.value.strokeStyle = config.color
  ctx.value.moveTo(x, y)
  ctx.value.lineTo(e.offsetX, e.offsetY)
  ctx.value.stroke()
  x.value = e.offsetX
  y.value = e.offsetY
}
function drawEnd () {
  x.value = 0
  y.value = 0
  isStart.value = false
  ctx.value.closePath()
}
function setConfig (v: Object) {
  config = v
}
onMounted (() => {
  ctx.value = canvas.value.getContext('2d')
})
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
    display: flex;
    flex-direction: column;
    flex: 1;
  }
  .layout-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .canvas {
      // width: 240px;
      // height: 240px;
      // border-radius: 8px;
      margin-top: 100px;
      // background-image: linear-gradient(90deg, #ffecd2, #fcb69f);
      background-color: #fff;
    }
    .btn-group {
      margin: 80px 0;
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

