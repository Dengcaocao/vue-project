<template>
  <header class="header">
    <div class="logo">
      <img :src="Logo" alt="icons8">
    </div>
    <h2 class="title">Avatar</h2>
    <div class="store-link">
      <a href="">
        <button class="store-link-btn">
          <img :src="GithubLogo" alt="github">
          <span>GitHub</span>
        </button>
      </a>
    </div>
  </header>
</template>
<script setup lang="ts">
import GithubLogo from '@/components/icons/icon-github.svg'
import Logo from '@/assets/logo.png'
</script>
<style scoped lang="scss">
@import '@/styles/var.scss';
.header {
  height: 88px;
  display: flex;
  align-items: center;
  padding: 0 30px;
  .logo {
    width: 40px;
    height: 40px;
    border-radius: 4px;
    background-image: linear-gradient(62deg, #8EC5FC, #E0C3FC);
    img {
      width: 100%;
      transform: scale(1.5);
    }
  }
  .title {
    margin-left: 15px;
    font-weight: bold;
    color: $color-text;
  }
  .store-link {
    margin-left: auto;
    a {
      text-decoration: none;
    }
    .store-link-btn {
      display: flex;
      align-items: center;
      border: none;
      outline: none;
      border-radius: 6px;
      padding: 8px 20px;
      background-color: $color-dark;
      cursor: pointer;
      span {
        margin-left: 4px;
        font-weight: bold;
        font-size: 16px;
        color: $color-text;
      }
    }
  }
}
</style>
