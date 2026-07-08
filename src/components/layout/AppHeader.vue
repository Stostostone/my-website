<script setup>
    import { ref } from 'vue'

    const emit = Object['menuSelect']

    function handleMenuClick() {
      emit('handleMenuClick');
    }
    function handleToolsClick() {
      emit('handleToolsClick');
    }
    function handleAboutClick() {
      emit('handleAboutClick');
    }

</script>
<template>
  <header class="header">
    <div class="header-content">
      <h1 @click="menuSelect()">石头屋</h1>
    </div>
    <ul class="switch-button">
      <li class="menu-button button" @click="handleMenuClick()">主页</li>
      <li class="tools-button button" @click="handleToolsClick()">工具箱</li>
      <li class="about-button button" @click="handleAboutClick()">关于我</li>
    </ul>
  </header>
</template>

<style scroped>
  .header {
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    background-color: rgba(255, 255, 255, 0.6);
    backdrop-filter: blur(10px);
    padding: 20px;
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

  }


</style>
