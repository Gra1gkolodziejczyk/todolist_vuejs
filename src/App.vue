<template>
  <div>
    <div class="flex flex-row justify-center text-center">
      <div class="pt-5 pl-3">
        <img src="../src/assets/logo.svg" alt="" width="33" height="33">
      </div>
      <h1 class="flex justify-center text-2xl font-bold pt-5">Liste des tâches à faire</h1>
      <div class="pt-5 pr-3">
        <img src="../src/assets/logo.svg" alt="" width="33" height="33">
      </div>
    </div>
    <AppForm @create="addTodo" @error="editError"></AppForm>
    <div class="flex justify-center text-center">
      <AppErrorText class="text-red-500" :message="errorMessage" v-if="errorMessage.length > 0"></AppErrorText>
    </div>
    <div class="flex flex-wrap justify-center">
      <div class="p-3" v-for="(todo, index) in todoList" :key="index">
        <AppTodoCard :todo="todo" v-model="todo.done" @delete="deleteTodo"></AppTodoCard>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';
import AppForm from './components/AppForm.vue';
import { TodoType } from '@/type/todo';
import AppTodoCard from './components/AppTodoCard.vue';
import AppErrorText from './components/AppErrorText.vue';

const todoList = reactive<TodoType[]>([])
const errorMessage = ref("");

function addTodo(newTodo: TodoType) {
  if (lastValidation(newTodo)) {
    errorMessage.value = ""
    todoList.push(newTodo)
  }
}

function deleteTodo(todoToRemove: TodoType) {
  const index = todoList.indexOf(todoToRemove);
  todoList.splice(index, 1);
}

function editError(message: string) {
  errorMessage.value = message;
}

// function editTodo(todoEdit: TodoType) {}

function lastValidation(newTodo: TodoType): boolean {
  let count = 0;
  let totalTime = newTodo.time;
  todoList.forEach(todo => {
    if (todo.user === newTodo.user) {
      count++;
      totalTime += todo.time
    }
  });
  if (count > 3) {
    errorMessage.value = "La personne à déjà 3 tâches."
    return false;
  }
  if (totalTime > 10) {
    errorMessage.value = "Le temps depassera 10h pour cette personne."
    return false;
  }
  return true;
}
</script>

<style scoped></style>
