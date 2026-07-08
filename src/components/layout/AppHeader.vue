<script setup>
    import { ref } from 'vue'

    const emit = defineEmits(['page-select'])

    function handleNavigationClick(name) {
      emit('page-select', name);
    }

</script>
<template>
  <header class="header">
    <div class="header-content">
      <h3 @click="handleNavigationClick('menu')">石头屋 | stone house</h3>
    </div>
    <ul class="switch-button">
      <li class="menu-button button" @click="handleNavigationClick('menu')">主页</li>
      <li class="tools-button button" @click="handleNavigationClick('tools')">工具箱</li>
      <li class="about-button button" @click="handleNavigationClick('about')">关于我</li>
    </ul>
  </header>
</template>

<style scoped>
  .header {
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    align-items: center;
    background-color: rgba(255, 255, 255, 0.6);
    backdrop-filter: blur(10px);
    padding: 14px;
    position: sticky;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    box-shadow: 0 0 20px rgba(15, 23, 42, 0.3);
  }

  .header-content {
    flex: 1;
    margin-right: auto;
    animation: fadeIn 0.4s ease;

  }

  .switch-button {
    display: flex;
    gap: 7px;
    justify-content: space-between;
    flex-direction: row;
    align-items: center;
    list-style: none;
    font-size: 12px;
  }


</style>
