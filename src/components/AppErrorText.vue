<script setup lang="ts">
interface Props {
  message: string
}
const {message} = defineProps<Props>()
</script>

<template>
  <div>
      <p className="text-red-500 text-sm">{{ message }}</p>
  </div>
</template>


<style scoped></style>