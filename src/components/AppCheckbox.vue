<script setup lang="ts">
  const done = defineModel<boolean>();
</script>

<template>
  <div class="">
      <input class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-green-300" type="checkbox" v-model="done" />
  </div>
</template>


<style scoped></style>