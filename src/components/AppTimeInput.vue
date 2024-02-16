<script setup lang="ts">
    interface Props {
        req: boolean
    }
    const {req} = defineProps<Props>();
    const time = defineModel();
</script>

<template>
  <div>
    <select 
        v-model="time" 
        :required="req" 
        class="mr-2 appearance-none bg-white border border-green-500 hover:border-green-800 rounded-md py-2 px-4 leading-normal focus:outline-none focus:border-green-800"
    >
        <option disabled value="">Heures</option>
        <option v-for="hour in 24" :key="hour" :value="hour">{{ hour }}</option>
    </select>
  </div>
</template>

<style scoped></style>