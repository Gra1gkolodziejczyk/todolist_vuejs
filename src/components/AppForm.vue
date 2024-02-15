<template>
  <div>
      <form :onsubmit="validateAndEmit">
          <AppInput v-model="title" :req="true" placeholder="Titre"></AppInput>
          <AppInput v-model="content" :req="true" placeholder="Contenu"></AppInput>
          <AppTimeInput v-model="time" :req="true" placeholder=""></AppTimeInput>
          <AppSelectList v-model="user" :req="true" :values="['Jean', 'Eric', 'Joe', 'Marco', 'Patrick']"></AppSelectList>
          <AppButton text="New todo" type="submit"></AppButton>
      </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import AppButton from './AppButton.vue';
import AppTimeInput from './AppTimeInput.vue';
import AppSelectList from './AppSelectList.vue';
import AppInput from './AppInput.vue';
import type { TodoType } from '@/type/todo';

const title = ref("");
const content = ref("");
const time = ref(0);
const id = ref(1);
const user = ref("");

type Emit = {
  create: [todo: TodoType]
  error: [message: string]
}
const emit = defineEmits<Emit>();

function validateAndEmit(event: SubmitEvent) {
  event.preventDefault();
  if (title.value === "") {
      emit("error", "Titre requit")
  } else if (content.value === "") {
      emit("error", "Contenu requit")
  } else if (time.value <= 0 || time.value > 10) {
      emit('error', 'Le temps doit être compris entre 1 et 10 inclus')
  } else if (user.value === "") {
    null
  } else {
      emit("create", {
          id: id.value++,
          title: title.value,
          content: content.value,
          time: time.value,
          done: false,
          user: user.value
      });
  }
}
</script>

<style scoped></style>