<script setup lang="ts">
import { ref } from 'vue';
import Upload from '../components/Upload.vue';
import Select from '../components/Select.vue';
import Button from '../components/Button.vue';

const language = ref('en');
const voice = ref('male');
</script>

<template>
  <div class="upload-view">
    <Upload class="upload-view__upload" />
    <div class="upload-view__settings">
      <Select
        label="Язык перевода"
        :options="[
          { value: 'en', label: 'Английский' },
          { value: 'ru', label: 'Русский' },
        ]"
        v-model="language"
      />
      <Select
        label="Голос"
        :options="[
          { value: 'male', label: 'Мужской' },
          { value: 'female', label: 'Женский' },
        ]"
        v-model="voice"
      />
    </div>
    <Button>Начать дубляж</Button>
  </div>
</template>

<style lang="scss" scoped>
.upload-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;

  &__upload {
    margin-bottom: 20px;
  }

  &__settings {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    width: 600px;
    margin-bottom: 20px;
  }
}
</style>
