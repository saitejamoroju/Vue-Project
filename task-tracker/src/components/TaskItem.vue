<template>
  <a-card
    style="margin-bottom: 8px; transition: all 0.3s;"
    :hoverable="true"
  >
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <div>
        <span>{{ task.title }}</span>
        <a-tag
          :color="task.status === 'Pending' ? 'orange' : 'green'"
          style="margin-left: 8px; transition: all 0.3s;"
        >
          {{ task.status }}
        </a-tag>
      </div>
      
      <a-button
        :type="task.status === 'Pending' ? 'default' : 'primary'"
        :icon="task.status === 'Pending' ? h(PlayCircleOutlined) : h(CheckCircleOutlined)"
        @click="$emit('toggle-status')"
        style="transition: all 0.3s;"
        size="small"
      >
        {{ task.status === 'Pending' ? 'Mark Done' : 'Mark Pending' }}
      </a-button>
    </div>
  </a-card>
</template>

<script setup>
import { h } from 'vue';
import { PlayCircleOutlined, CheckCircleOutlined } from '@ant-design/icons-vue';

defineProps(['task']);
defineEmits(['toggle-status']);
</script>