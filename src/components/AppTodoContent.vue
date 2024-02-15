<script setup lang="ts">
interface Props {
  text: string
}
const {text} = defineProps<Props>()
</script>

<template>
  <div>
      <p>{{ text }}</p>
  </div>
</template>

<style scoped></style>