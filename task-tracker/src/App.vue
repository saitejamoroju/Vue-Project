<template>
  <a-card title="Task Tracker" style="width: 500px; margin: auto; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);">
    <AddTaskForm @add-task="addTask" />
    <FilterButtons :currentFilter="filter" @change-filter="filter = $event" />
    <TaskList :tasks="filteredTasks" @toggle-status="toggleStatus" />
    <TaskCounter :count="filteredTasks.length" />
  </a-card>
</template>

<script setup>
import { ref, computed } from 'vue';
import AddTaskForm from './components/AddTaskForm.vue';
import FilterButtons from './components/FilterButtons.vue';
import TaskList from './components/TaskList.vue';
import TaskCounter from './components/TaskCounter.vue';

const tasks = ref([]);
const filter = ref('All');

const addTask = (title) => {
  tasks.value.push({ id: Date.now(), title, status: 'Pending' });
};

const toggleStatus = (id) => {
  const task = tasks.value.find((t) => t.id === id);
  if (task) task.status = task.status === 'Pending' ? 'Completed' : 'Pending';
};

const filteredTasks = computed(() => {
  console.log('filteredTasks computed, filter:', filter.value, 'tasks:', tasks.value); // Debug log
  if (filter.value === 'All') return tasks.value;
  return tasks.value.filter((t) => t.status === filter.value);
});
</script>