<template>
  <div style="margin-bottom: 16px">
    <a-input
      v-model:value="title"
      placeholder="Enter task"
      style="width: 70%; margin-right: 8px"
      :allow-clear="true"
      @keyup.enter="submitTask"
    />

    <a-button type="primary" @click="submitTask" style="transition: all 0.3s">
      Add
    </a-button>
  </div>
</template>

<script setup>
import { ref } from "vue";
const title = ref("");
const emit = defineEmits(["add-task"]);

const submitTask = () => {
  if (title.value.trim()) {
    emit("add-task", title.value);
    title.value = "";
  }
};
</script>
