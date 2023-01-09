<template>
  <div class="layout">
    <Header />
    <slot />
    <Footer />
  </div>
</template>
<script setup lang="ts">
import Header from './header.vue'
import Footer from './footer.vue'
</script>