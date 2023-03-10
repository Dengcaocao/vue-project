<template>
  <Layout>
    <div class="warp">
      <canvas class="canvas" ref="canvas" :width="cvsW" :height="cvsH"></canvas>
      <div class="action">
        <button class="upload" ref="upload" @click="uploadFile">
          <img src="@/assets/upload.svg" />
          上传图片
        </button>
        <input style="display: none;" type="file" ref="file" @change="getFile">
        <button class="download" ref="download">
          <img src="@/assets/download.svg" />
          下载
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

const getFile = e => {
  let width: number = 0
  let height: number = 0
  const file: File = e.target.files[0]
  const url: string = URL.createObjectURL(file)
  const image: HTMLImageElement = new Image()
  image.src = url
  image.onload = () => {
    if (image.width < window.innerWidth && image.height < window.innerHeight - 88) {
      width = image.width
      height = image.height
    }
    if (image.width > image.height) {
      width = window.innerWidth
      height = window.innerWidth * image.height / image.width
    } else {
      height = window.innerHeight
      width = window.innerHeight * image.width / image.height
    }
    cvsW.value = width
    cvsH.value = height
    setTimeout(() => {
      drawImage(image, width, height)
    }, 0)
  }
}

const canvas: any = ref(null)
const drawImage = (img: HTMLImageElement, width: number, height: number) =>  {
  const ctx: CanvasRenderingContext2D = canvas.value.getContext('2d')
  ctx.drawImage(img, 0, 0, width, height)
}
</script>

<style scoped lang="scss">
.warp {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  .canvas {
    background-color: #fff;
  }
  .action {
    position: absolute;
    top: 30px;
    right: 30px;
    button {
      border: 0;
      outline: none;
      font-size: 16px;
      padding: 6px 12px;
      cursor: pointer;
      color: var(--color-text);
      background-color: var(--vt-c-text-light-2);
      img {
        width: 26px;
        vertical-align: middle;
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
