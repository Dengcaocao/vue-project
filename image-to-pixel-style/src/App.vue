<template>
  <Layout>
    <div class="warp">
      <canvas class="canvas" ref="canvas" :width="cvsW" :height="cvsH"></canvas>
      <div class="action">
        <button class="upload" ref="upload" @click="uploadFile">
          <img src="@/assets/upload.svg" />
          <span>上传图片</span>
        </button>
        <input style="display: none;" type="file" ref="file" @change="getFile">
        <button class="download" ref="download">
          <img src="@/assets/download.svg" />
          <span>下载</span>
        </button>
      </div>
    </div>
  </Layout>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Layout from './components/layout/index.vue'

let cvsW = ref(0)
let cvsH = ref(0)

const file: any = ref(null)
const uploadFile = () => {
  file.value.click()
}

interface ISizeInfo {
  type: string,
  value: number
}
const getFile = e => {
  const file: File = e.target.files[0]
  const url: string = URL.createObjectURL(file)
  const image: HTMLImageElement = new Image()
  image.src = url
  image.onload = () => {
    // // 计算宽高比
    const imgScale: number = image.width / image.height
    // 取最小值
    const sizeInfo: ISizeInfo = window.innerWidth > (window.innerHeight - 88)
      ? { type: 'height', value: window.innerHeight - 88 }
      : { type: 'width', value: window.innerWidth }
    // 减去头部得到的高度
    const height = window.innerHeight - 88
    if (sizeInfo.type === 'width') {
      // 根据比例算出窗口需要的高度
      const winNeedHeight: number = sizeInfo.value / imgScale
      if (winNeedHeight > height) {
        cvsW.value = height * imgScale
        cvsH.value = height
      } else {
        cvsW.value = sizeInfo.value
        cvsH.value = window.innerHeight > winNeedHeight ? winNeedHeight : window.innerHeight
      }
    } else {
      // 根据比例算出窗口需要的宽度
      const winNeedWidth: number = sizeInfo.value * imgScale
      if (winNeedWidth > window.innerWidth) {
        cvsW.value = winNeedWidth
        cvsH.value = window.innerWidth / imgScale
      } else {
        cvsH.value = sizeInfo.value
        cvsW.value = window.innerWidth > winNeedWidth ? winNeedWidth : window.innerWidth
      }
    }
    setTimeout(() => drawImage(image, cvsW.value, cvsH.value), 0)
  }
}

const canvas: any = ref(null)
const drawImage = (img: HTMLImageElement, width: number, height: number) =>  {
  const ctx: CanvasRenderingContext2D = canvas.value.getContext('2d')
  ctx.drawImage(img, 0, 0, width, height)
  const pxMap = createPxMap(ctx)
  drawPXCanvas(pxMap)
}

const size = 8
interface IColorblock {
  x: number,
  y: number,
  color: string
}
function createPxMap (ctx){
  const pxMap: IColorblock[] = []
  for (let i = 0; i < cvsW.value; i += size) {
    for (let j = 0; j < cvsH.value; j += size) {
      const pixel = ctx.getImageData(i, j, 1, 1).data
      const color = `rgba(${pixel[0]}, ${pixel[1]}, ${pixel[2]}, ${pixel[3]/255})`
      pxMap.push({
        x: i / size,
        y: j / size,
        color
      })
     }
   }
  return pxMap
}

function drawPXCanvas (pxMap) {
  const ctx = canvas.value.getContext('2d')
  pxMap.forEach(px => {
    const { color, x, y } = px
    ctx.fillStyle = color
    ctx.fillRect(x * size, y * size, size, size)
   })
}
</script>

<style scoped lang="scss">
.warp {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  .canvas {
    background-color: #fff;
  }
  .action {
    position: absolute;
    top: 30px;
    right: 30px;
    display: flex;
    align-items: center;
    button {
      overflow: hidden;
      display: flex;
      align-items: center;
      border: 0;
      outline: none;
      font-size: 16px;
      padding: 6px 12px;
      cursor: pointer;
      color: #fff;
      border-radius: 4px;
      background-color: #41474d;
      img {
        width: 26px;
        filter: drop-shadow(#fff 100px 0);
        transform: translateX(-100px);
      }
    }
    .upload {
      margin-right: 20px;
    }
  }
}
@media (min-width: 1024px) {
  /* header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  } */
}
</style>
