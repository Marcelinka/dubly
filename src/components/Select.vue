<script setup lang="ts">
import { useId } from 'vue';
import ArrowDownIcon from '@/assets/icons/arrow-down.svg';

export interface SelectOption {
  value: string;
  label: string;
}

const props = defineProps<{
  options: SelectOption[];
  placeholder?: string;
  disabled?: boolean;
  label?: string;
}>();

const model = defineModel<string>();
const id = useId();
</script>

<template>
  <div class="select">
    <label :for="id" class="select__label">{{ label }}</label>
    <div class="select__wrapper">
      <select :id="id" v-model="model" :disabled="disabled" class="select__input">
        <option v-if="placeholder" value="" disabled>{{ placeholder }}</option>
        <option v-for="option in options" :key="option.value" :value="option.value">
          {{ option.label }}
        </option>
      </select>
      <span class="select__icon">
        <ArrowDownIcon class="select__icon-svg" width="30" height="30" />
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.select {
  display: flex;
  flex-direction: column;
  gap: 8px;

  &__label {
    font-size: 14px;
    font-weight: 500;
    width: 100%;
  }

  &__wrapper {
    position: relative;
    width: 100%;
  }

  &__input {
    width: 100%;
    padding: 8px;
    border-radius: 8px;
    border: 1px solid #5865f2;
    background-color: #161b22;
    color: #f0f6fc;
    font-size: 14px;
    outline: none;
    cursor: pointer;
    transition: border-color 0.2s ease-in-out;
    padding-inline: 16px;
    padding-block: 12px;
    appearance: none;
    padding-right: 40px;
  }

  &__icon {
    position: absolute;
    right: 5px;
    top: 50%;
    transform: translateY(-50%);
    pointer-events: none;
    line-height: 0;
  }
}
</style>
