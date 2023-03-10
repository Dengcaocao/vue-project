<template>
  <div class="layout">
    <Hearder />
    <Container>
      <slot></slot>
    </Container>
  </div>
</template>
<script setup lang="ts">
import Hearder from './hearder.vue'
import Container from './container.vue'
</script>
<style scoped>
.layout {
  height: 100vh;
  display: flex;
  flex-direction: column;
}
.layout .container {
  flex: 1;
  height: 0;
  overflow-y: auto;
}
</style>
