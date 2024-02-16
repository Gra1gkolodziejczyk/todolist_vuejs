<script setup lang="ts">
interface Props {
  text: string
  class: string
}
const {text} = defineProps<Props>()
</script>

<template>
  <div>
      <span>{{ text }}</span>
  </div>
</template>

<style scoped></style>