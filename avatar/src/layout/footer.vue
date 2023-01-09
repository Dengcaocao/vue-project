<template>
  <footer class="footer">
    <a href="">Deng·草草</a>
  </footer>
</template>
<style scoped lang="scss">
@import '@/styles/var.scss';
.footer {
  padding-bottom: 15px;
  text-align: center;
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