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
  <div>
    <AppTodoTitle :title="todo.title"></AppTodoTitle>
    <AppTodoContent :text="todo.content"></AppTodoContent>
    <AppTodoCardText :text="'Estimated time : ' + todo.time + ' h'"></AppTodoCardText>
    <AppTodoCardText :text="'Assign : ' + todo.user"></AppTodoCardText>
    <AppCheckbox v-model="done"></AppCheckbox>
    <AppButton text="Supprimer" type="button" @click="$emit('delete', todo)"></AppButton>
  </div>
</template>

<style scoped></style>