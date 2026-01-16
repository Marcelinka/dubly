<script setup lang="ts">
defineProps<{
  type?: 'button' | 'submit' | 'reset';
  disabled?: boolean;
}>();
</script>

<template>
  <button :type="type ?? 'button'" :disabled="disabled" class="button">
    <slot></slot>
  </button>
</template>

<style lang="scss" scoped>
.button {
  font-weight: 500;
  font-size: 16px;
  background-color: #5865f2;
  border: none;
  border-radius: 8px;
  padding-inline: 16px;
  padding-block: 12px;
  color: #f0f6fc;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;

  &:hover {
    background-color: #4752c4;
  }

  &:disabled {
    background-color: #99a1af;
  }
}
</style>
