<script setup lang="ts">
  interface Props {
      values: string[],
      req: boolean
  }
  const {values, req} = defineProps<Props>();

  const selection = defineModel();
</script>

<template>
  <div>
      <select v-model="selection" :required="req">
          <option v-for="(value, index) in values" :key="index" :value="value" />
      </select>
  </div>
</template>

<style scoped></style>