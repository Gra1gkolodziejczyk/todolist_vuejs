<script setup lang="ts">
  interface Props {
      title: string
  }
  const {title} = defineProps<Props>()
</script>

<template>
  <div class="flex justify-center text-center">
      <h1 className="text-xl font-bold">{{ title }}</h1>
  </div>
</template>

<style scoped></style>