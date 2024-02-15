<script setup lang="ts">
  interface Props {
      title: string
  }
  const {title} = defineProps<Props>()
</script>

<template>
  <div>
      <h1>{{ title }}</h1>
  </div>
</template>

<style scoped></style>