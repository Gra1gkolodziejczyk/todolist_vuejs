<template>
  <div>
      <form class="flex justify-center text-center flex-col pr-96 pl-96" :onsubmit="validateAndEmit">
          <div class="pt-3 pb-3">
            <AppInput v-model="title" :req="true" placeholder="Titre"></AppInput>
          </div>
          <div class="pt-3 pb-3">
            <AppInput v-model="content" :req="true" placeholder="Contenu"></AppInput>
          </div>
          <div class="pt-3 pb-3 flex flex-row justify-center text-center">
          <h3 class="flex justify-center text-center pt-2 pr-3">Temps aloué à cette tâche: </h3>
            <AppTimeInput v-model="time" :req="true" placeholder=""></AppTimeInput>
          </div>
          <div class="pt-3 pb-3">
            <AppSelectList v-model="user" :req="true" :values="['Jean', 'Eric', 'Joe', 'Marco', 'Patrick']"></AppSelectList>
          </div>
          <div class="pt-3 pb-3">
            <AppButton text="New todo" type="submit"></AppButton>
          </div>
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
    emit("error", "La personne à déjà 3 tâches.")
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