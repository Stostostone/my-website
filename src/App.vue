<script setup>
import AppHeader from '@/components/layout/AppHeader.vue';
import MenuPage from '@/components/layout/MenuPage.vue';
</script>

<template>
  <div class="app-layout">
    <AppHeader />
    <MenuPage />
  </div>
</template>

<style scoped>
  .app-layout {
    display: grid;
    grid-template-rows: auto 1fr auto;
    min-height: 150vh;
    padding-top: header-height;
  }

</style>
