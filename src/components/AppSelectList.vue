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
    <select 
      v-model="selection" 
      :required="req" 
      class="appearance-none bg-white border border-green-500 hover:border-green-500 rounded-md py-2 px-4 block w-full leading-normal focus:outline-none focus:border-green-800"
    >
      <option disabled value="">Sélectionner un responsable</option>
      <option v-for="(value, index) in values" :key="index" :value="value">{{ value }}</option>
    </select>
  </div>
</template>

<style scoped></style>