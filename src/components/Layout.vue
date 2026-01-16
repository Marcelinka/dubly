<script setup lang="ts">
import Button from './Button.vue';
import Link from './Link.vue';
</script>

<template>
  <div class="layout">
    <header class="header">
      <div class="header__logo">Dubly</div>
      <Button>Помощь</Button>
    </header>
    <main class="main">
      <slot />
    </main>
    <footer class="footer">
      <Link href="#">Пользовательское соглашение</Link>
    </footer>
  </div>
</template>

<style lang="scss" scoped>
.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;
  max-height: 100vh;
  background-color: #0b0e14;
  color: #f0f6fc;
}

.header {
  height: 75px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #161b22;
  padding-inline: 64px;

  &__logo {
    font-size: 40px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: -0.03em;
  }
}

.main {
  flex: 1;
  overflow-x: auto;
}

.footer {
  background-color: #161b22;
  height: 75px;
  display: flex;
  align-items: center;
  padding-inline: 64px;
}
</style>
