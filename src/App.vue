<script setup>
import AppHeader from '@/components/layout/AppHeader.vue';
import MenuPage from '@/components/layout/MenuPage.vue';
import LoadingPage from '@/components/loading/LoadingPage.vue';
import ToolsPage from '@/components/layout/ToolsPage.vue';
import AboutPage from '@/components/layout/AboutPage.vue'
import { ref } from 'vue';

const menuSelected = ref(true);
const toolsSelected = ref(false);
const aboutSelected = ref(false);

function handleNavigationClick(pageName) {
  console.log('点击了：', pageName);
  menuSelected.value = pageName === 'menu';
  toolsSelected.value = pageName === 'tools';
  aboutSelected.value = pageName === 'about';
}

</script>

<template>
  <div class="app-layout">
    <AppHeader @page-select = "handleNavigationClick"/>
    <MenuPage v-if="menuSelected"/>
    <ToolsPage v-if="toolsSelected"/>
    <AboutPage v-if="aboutSelected"/>
  </div>


  <!-- <div class="app-layout">
    <LoadingPage />
  </div> -->

</template>

<style scoped>
  .app-layout {
    display: grid;
    grid-template-rows: auto 1fr auto;
    position: relative;
  }

</style>
