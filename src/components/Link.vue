<script setup lang="ts">
defineProps<{
  href: string;
  target?: '_blank' | '_self' | '_parent' | '_top';
}>();
</script>

<template>
  <a :href="href" :target="target" class="link">
    <slot></slot>
  </a>
</template>

<style lang="scss" scoped>
.link {
  font-weight: 600;
  font-size: 16px;
  text-decoration: underline;
  color: #f0f6fc;
  cursor: pointer;
  transition: color 0.2s ease-in-out;

  &:hover {
    color: #5865f2;
  }
}
</style>
