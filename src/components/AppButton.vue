<script setup lang="ts">
interface Props {
    text: string,
    type: "button" | "submit" | "reset" | undefined,
}
const {text, type} = defineProps<Props>();
</script>

<template>
  <div>
    <button :type="type">{{ text }}</button>
  </div>
</template>

<style scoped></style>
