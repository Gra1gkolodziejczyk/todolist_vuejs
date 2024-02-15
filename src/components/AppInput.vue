<script setup lang="ts">
  interface Props {
      placeholder?: string
      req?: boolean
  }

  const {placeholder, req} = defineProps<Props>()

  const text = defineModel<string>()
</script>

<template>
  <div>
      <input type="text" :placeholder="placeholder" :required="req" v-model="text" />
  </div>
</template>

<style scoped></style>