<template>
  <div style="margin-top: 16px; font-size: 16px; font-weight: bold;">
    <transition name="fade">
      <span>Total Tasks: {{ count }}</span>
    </transition>
  </div>
</template>

<script setup>
defineProps(['count']);
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>