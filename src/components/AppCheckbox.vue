<script setup lang="ts">
  const done = defineModel<boolean>();
</script>

<template>
  <div>
      <input type="checkbox" v-model="done" />
  </div>
</template>


<style scoped></style>