<script setup lang="ts">
import TodoItem from '~/components/TodoItem.vue';
import type { Todo } from '~/interfaces/Todo';

const todos = ref<Todo[]>([])
const newTodo = ref('')

function addTodo() {
  if (newTodo.value == '')
    return
  todos.value.push({
    id: Date.now(),
    text: newTodo.value,
    completed: false
  })
  newTodo.value = ''
}

function deleteTodo(id: number) {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

</script>
<template>
  <v-container class="align-center">
    <v-row align="center">
      <v-col align="center">
        <h1>My Brainzzzz</h1>
        <v-text-field v-model="newTodo" @keyup.enter="addTodo"></v-text-field>
        <v-list>
          <TodoItem
            v-for="todo in todos.slice().reverse()"
            :key="todo.id"
            :todo="todo"
            @delete="deleteTodo"
          />
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>
