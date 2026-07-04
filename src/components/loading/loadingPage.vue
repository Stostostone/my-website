<script setup>

</script>

<template>
  <div class="loading-page is-active">
    <div class="loading-content">
      <div class="loading-spinner"></div>
      <p>Loading</p>
    </div>
  </div>
</template>

<style>
  .loading-page {
    display: grid;
    place-items: center;
    width: 100%;
    min-height: 100vh;
  }

  .loading-content {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    justify-content: center;
    text-align: center;
    align-items: center;
    position: relative;
  }

  .loading-content::after {
    content: '';
    position: absolute;
    width: 100vw;
    height: 10%;
    background-color: rgba(116, 0, 0, 0.089);
    backdrop-filter: blur(10px);
    
    margin-top: 10px;
    z-index: -1;
  }

  .loading-spinner {
    width: 300px;
    height: 2px;
    border: none;
    margin-bottom: 10px;
    background-color: #ffffff;
    background: linear-gradient(
      to right,
      rgb(255, 255, 255, 0.7) ,
      rgb(255, 187, 187, 0.7),
      rgb(255, 231, 231, 0.7),
      rgba(255, 108, 108, 0.7),
      rgba(255, 235, 235, 0.7)
    );
    animation: loading 5s linear;
  }

  @keyframes loading {
    0% {
      clip-path: inset(0 100% 0 0);
    }
    50% {
      clip-path: inset(0 20% 0 0);
    }
    100% {
      clip-path: inset(0 0 0 0);
    }
  }
</style>
