<template>
  <footer class="footer">
    <a href="">Deng·草草</a>
  </footer>
</template>
<style scoped lang="scss">
@import '@/styles/var.scss';
.footer {
  text-align: center;
  margin-bottom: 20px;
  a {
    text-decoration: none;
    color: $color-text;
    font-weight: bold;
    &:hover {
      color: lighten($color-text, 10);;
    }
  }
}
</style>