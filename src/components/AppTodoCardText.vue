<script setup lang="ts">
interface Props {
  text: string
}
const {text} = defineProps<Props>()
</script>

<template>
  <div>
      <span>{{ text }}</span>
  </div>
</template>

<style scoped></style>