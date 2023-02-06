<template>
  <div class="section">
    <h3>{{props.title}}</h3>
    <slot />
  </div>
</template>
<script setup lang="ts">
const props = defineProps<{
  title: String
}>()
</script>
<style scoped lang="scss">
@import '../styles/var.scss';
.section {
  margin-bottom: 25px;
  h3 {
    color: $color-text;
    font-weight: bold;
    padding-bottom: 15px;
  }
}
</style>