<script setup>
import AppHeader from '@/components/layout/AppHeader.vue';
import MenuPage from '@/components/layout/MenuPage.vue';
import LoadingPage from '@/components/loading/LoadingPage.vue';
import ToolsPage from './components/layout/ToolsPage.vue';
import { ref } from 'vue';

const menuSelected = ref(true);
const toolsSelected = ref(false);
const aboutSelected = ref(false);
const navigationIndex = ref([]);

navigationIndex.value[0] = 'menuSelected';
navigationIndex.value[1] = 'toolsSelected';
navigationIndex.value[2] = 'aboutSelected'

function handleNavigationClick(event) {
  for (let i = 0; i < navigationIndex.value.length; i++) {

  }
  menuSelect.value = true;
  toolsSelect.value = false;
}

</script>

<template>
  <div class="app-layout">
    <!-- <AppHeader @menuSelected = "handleNavigationClick(event)"/> -->
     <AppHeader />
    <MenuPage v-if="menuSelected"/>
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
