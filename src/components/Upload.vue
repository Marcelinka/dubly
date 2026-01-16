<script setup lang="ts">
import { ref } from 'vue';
import UploadIcon from '@/assets/icons/upload.svg';
import Button from './Button.vue';

const emit = defineEmits<{
  upload: [file: File];
}>();

const fileInput = ref<HTMLInputElement | null>(null);
const isDragging = ref(false);

const handleDragOver = (event: DragEvent) => {
  event.preventDefault();
  isDragging.value = true;
};

const handleDragLeave = () => {
  isDragging.value = false;
};

const handleDrop = (event: DragEvent) => {
  event.preventDefault();
  isDragging.value = false;

  const file = event.dataTransfer?.files?.[0];
  if (file && file.type.startsWith('video/')) {
    emit('upload', file);
  }
};

const handleFileSelect = (event: Event) => {
  const target = event.target as HTMLInputElement;
  const file = target.files?.[0];
  if (file) {
    emit('upload', file);
  }
};

const openFileDialog = () => {
  fileInput.value?.click();
};
</script>

<template>
  <div
    class="upload-dropzone"
    :class="{ 'is-dragging': isDragging }"
    @dragover="handleDragOver"
    @dragleave="handleDragLeave"
    @drop="handleDrop"
  >
    <input
      ref="fileInput"
      type="file"
      accept="video/*"
      class="upload-input"
      @change="handleFileSelect"
    />
    <UploadIcon class="upload-icon" width="70" />
    <Button @click="openFileDialog">Загрузить видео</Button>
  </div>
</template>

<style lang="scss" scoped>
.upload-dropzone {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 300px;
  width: 600px;
  background-color: #161b22;
  border-radius: 12px;
  border: 2px dashed #5865f2;
  transition:
    border-color 0.2s ease-in-out,
    background-color 0.2s ease-in-out;

  &.is-dragging {
    border-color: #4752c4;
    background-color: #1c2128;
  }
}

.upload-input {
  display: none;
}
</style>
