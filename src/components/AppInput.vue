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
      <input 
        class="bg-green-300 border border-green-500 text-black text-sm rounded-lg focus:ring-green-500 focus:border-green-500 block w-full p-2.5 placeholder:text-black" 
        type="text" 
        :placeholder="placeholder" 
        :required="req" 
        v-model="text" 
      />
  </div>
</template>

<style scoped></style>