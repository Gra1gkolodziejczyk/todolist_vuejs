<script setup lang="ts">
interface Props {
  message: string
}
const {message} = defineProps<Props>()
</script>

<template>
  <div>
      <p>{{ message }}</p>
  </div>
</template>


<style scoped></style>