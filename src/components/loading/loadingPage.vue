<script setup>
import WaterWave from '../WaterWave.vue';


</script>

<template>
  <div class="loading-page is-active">
    <div class="loading-content">
      <!-- <div class="loading-spinner"></div>
      <p>Loading</p> -->
      <WaterWave />
    </div>
  </div>
</template>

<style scoped>
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
    height: 20%;
    background-color: rgba(116, 0, 0, 0.089);
    backdrop-filter: blur(20px);
    background: rgba(59, 0, 0, 0.034);
    mask-image: linear-gradient(
      to bottom,
      transparent 0%,
      black 20%,
      black 80%,
      transparent 100%
        );
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
      rgba(255, 224, 224, 0.407) ,
      rgba(255, 108, 108, 0.327),
      rgba(0, 71, 193, 0.201),
      rgba(255, 187, 187, 0.7),
      rgba(0, 4, 255, 0.197)
    );
    animation: loading 7s linear;
  }

  @keyframes loading {
    0% {
      clip-path: inset(0 100% 0 0);
    }
    20% {
      clip-path: inset(0 80% 0 0);
    }
    50% {
      clip-path: inset(0 50% 0 0);
    }
    100% {
      clip-path: inset(0 0 0 0);
    }
  }
</style>
