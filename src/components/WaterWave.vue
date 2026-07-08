<script setup>
  import {  ref, onMounted, onUnmounted } from 'vue';

  let id = 0;
  let timer = null;
  const drops = ref([]);
  const canvasRef = ref(null);


  function createWaterWave() {
    const drop = {
      id: id++,
      x: Math.random() * 100,
      y: Math.random() * 100,
      radius: Math.random() * 10 + 5,
      speed: Math.random() * 0.5 + 0.5,
      opacity: Math.random() * 0.5 + 0.5,
      size: Math.random() * 5 + 5,
      duration: Math.random() * 1000 + 1000,
    }

    drops.value.push(drop);

    setTimeout(() => {
      drops.value = drops.value.filter(d => d.id !== drop.id);
    }, drop.duration + 800);
  }

  onMounted(() => {
    timer = setInterval(createWaterWave, 350);
  });

  onUnmounted(() => {
    clearInterval(timer);
  });

  const canvas = document.getElementById('canvas')
  const ctx = canvas.getContext('2d')
</script>

<canvas id="reflection" >

</canvas>

<template>
  <div class="drop">

  </div>
</template>

<style scoped>
  .drop {
    width: 500px;
    height: 500px;
    position: relative;
  }

  .drop::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 50%;

    width: 15px;
    height: 15px;

    border: 1px solid rgba(255, 255, 255, 0.7);
    border-radius: 50%;

    transform: translate(-50%, -50%) scale(0);
    opacity: 0;
    animation: ripple 2s ease-out infinite;
  }

  @keyframes ripple {
  0% {
    transform: translate(-50%, -50%) scale(0);
    opacity: 0;
  }

  20% {
    opacity: 0.8;
  }

  100% {
    transform: translate(-50%, -50%) scale(6);
    opacity: 0;
  }
}
</style>


