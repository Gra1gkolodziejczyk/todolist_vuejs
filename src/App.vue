<script setup lang="ts">
import { ref, onMounted, watch } from "vue";

interface Todo {
  todo: string;
  done: boolean;
}

const todos = ref<Todo[]>([]);
const text = ref<string>("");
const inputError = ref<boolean>(false);

function addTodo() {
  if (text.value.trim() === "") {
    inputError.value = true;
    return;
  } else {
    inputError.value = false;
  }

  todos.value.unshift({
    todo: text.value,
    done: false,
  });

  text.value = "";
}

function deleteTodo(todo: Todo) {
  todos.value = todos.value.filter((x) => x !== todo);
}

watch(
  todos,
  (newTodoValue) => {
    localStorage.setItem("todos", JSON.stringify(newTodoValue));
  },
  { deep: true }
);

onMounted(() => {
  const savedTodos = localStorage.getItem("todos");
  if (savedTodos) {
    todos.value = JSON.parse(savedTodos) as Todo[];
  }
});
</script>

<template>
  <main class="app">
    <section class="greeting">
    </section>

    <div class="input-section">
      <section class="create-todo">
        <h3>Ajouter une tâche</h3>
        <form class="form" @submit.prevent="addTodo">
          <input
            type="text"
            placeholder="écrit la tâche à faire"
            v-model="text"
          />

          <div class="input-add">
            <input type="submit" value="Ajouter" />
          </div>
        </form>
        <span v-if="inputError" class="error-message">Veuillez entrer une tâche avant d'ajouter</span>
      </section>
    </div>
    <div class="todo-section">
      <section class="todo-list">
        <h2 v-show="todos.length === 0">Pas encore de tâches...</h2>

        <div class="list">
          <div :key="todo.todo" v-for="todo in todos" :class="`todo-item ${todo.done && 'done'}`">
            <label class="label">
              <input type="checkbox" v-model="todo.done" />
            </label>

            <div class="todo-content">
              <input type="text" v-model="todo.todo"/>
            </div>

            <div class="action-delete">
              <button class="delete" @click="deleteTodo(todo)">Supprimer</button>
            </div>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<style>
.app {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 10%;
}

.todo-item {
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}

.error-message {
  color: red;
}

.form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}

.input-add {
  padding-left: 10px;
}

.label {
  padding-right: 10px;
}

.action-delete {
  padding-left: 10px;
}
</style>
