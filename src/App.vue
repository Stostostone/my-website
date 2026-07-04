<script setup>
import AppHeader from '@/components/layout/AppHeader.vue';
import MenuPage from '@/components/layout/MenuPage.vue';
import LoadingPage from '@/components/loading/LoadingPage.vue';
</script>

<template>
  <!-- <div class="app-layout">
    <AppHeader />
    <MenuPage />
  </div> -->
  <div class="app-layout">
    <LoadingPage />
  </div>
</template>

<style scoped>
  .app-layout {
    display: grid;
    grid-template-rows: auto 1fr auto;
    padding-top: header-height;
  }

</style>
