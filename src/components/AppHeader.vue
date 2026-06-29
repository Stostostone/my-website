<script setup>
    import { ref } from 'vue'

    const headerTitle = ref('石头屋')

    function updateHeaderTitle(newTitle) {
        headerTitle.value = newTitle
    }
    function changePage() {
      
    }

</script>
<template>
  <header class="header">
    <div class="header-content">
      <h1>{{ headerTitle }}</h1>
    </div>
    <div class="switch-button">
      <button class="menu-button button">
        主页
      </button>
      <button class="tools-button button">
        工具箱
      </button>
      <button class="about-button button">
        关于我
      </button>
    </div>
  </header>
</template>

<style>
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
  }


</style>
