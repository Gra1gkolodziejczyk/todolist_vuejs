<script setup lang="ts">
import AppTodoTitle from './AppTodoTitle.vue';
import type { TodoType } from '../type/todo';
import AppTodoContent from './AppTodoContent.vue';
import AppTodoCardText from './AppTodoCardText.vue';
import AppButton from './AppButton.vue';
import AppCheckbox from './AppCheckbox.vue';

const done = defineModel<boolean>()

interface Props {
  todo: TodoType
}
const {todo} = defineProps<Props>()

type Emit = {
  delete: [todo: TodoType]
}
defineEmits<Emit>();
</script>

<template>
  <div class="flex justify-center text-center flex-col border border-green-500 rounded p-4 max-w-xs">
    <AppTodoTitle :title="todo.title"></AppTodoTitle>
    <AppTodoContent :text="todo.content"></AppTodoContent>
    <AppTodoCardText class="font-thin" :text="'Temps estimé : ' + todo.time + ' h'"></AppTodoCardText>
    <AppTodoCardText class="font-bold" :text="'La tâche est faite par : ' + todo.user"></AppTodoCardText>
    <AppCheckbox v-model="done"></AppCheckbox>
    <div class="flex flex-row justify-center text-center">
      <div class="pt-3 pr-3">
      <AppButton text="Supprimer" type="button" @click="$emit('delete', todo)"></AppButton>
    </div>
    <div class="pt-3">
      <AppButton text="Editer" type="button" @click="$emit('delete', todo)"></AppButton>
    </div>
    </div>
  </div>
</template>

<style scoped></style>