<script setup lang="ts">
import type { Todo } from '@/interfaces/Todo'

defineProps<{
  todo: Todo,
}>()
</script>

<template>
  <v-list-item :value="todo.id">
    <template v-slot:prepend="{ isActive }">
      <v-list-item-action start>
        <v-checkbox-btn :model-value="isActive"></v-checkbox-btn>
      </v-list-item-action>
    </template>
    <div class="d-flex align-center justify-space-between">
      <v-list-item-title class="text-body-1">{{todo.text}}</v-list-item-title>
      <v-btn @click="$emit('delete', todo.id)">Delete</v-btn>
    </div>
  </v-list-item>
</template>
