<template>
  <div style="margin-bottom: 16px;">
    <a-button-group>
      <a-button
        :type="currentFilter === 'All' ? 'primary' : 'default'"
        @click="$emit('change-filter', 'All')"
        style="transition: all 0.3s;"
      >
        All
      </a-button>
      <a-button
        :type="currentFilter === 'Pending' ? 'primary' : 'default'"
        @click="$emit('change-filter', 'Pending')"
        style="transition: all 0.3s;"
      >
        Pending
      </a-button>
      <a-button
        :type="currentFilter === 'Completed' ? 'primary' : 'default'"
        @click="$emit('change-filter', 'Completed')"
        style="transition: all 0.3s;"
      >
        Completed
      </a-button>
    </a-button-group>
  </div>
</template>

<script setup>
defineProps(['currentFilter']);
defineEmits(['change-filter']);
</script>