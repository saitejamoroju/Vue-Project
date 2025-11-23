
<template>
    <div>
      <TaskItem v-for="task in tasks" :key="task.id" :task="task" @toggle-status="$emit('toggle-status', task.id)" />
    </div>
  </template>
  
  <script setup>
  import TaskItem from './TaskItem.vue';
  defineProps(['tasks']);
  defineEmits(['toggle-status']);
  </script>
  