<script setup>
  import { ref } from 'vue';

  const emit = defineEmits(['open']);

  function openDrawBoard() {
    emit('open');
  }

</script>

<template>
  <div class="draw-board-card card" @click="openDrawBoard()">
    <div class="card-header">
        <h3 class="title">Canvas 画板</h3>
        <p class="draw-label label">在这里你可以自由绘画，创作属于你的艺术作品</p>
    </div>
    <span class="line"></span>
    <div class="card-img">
      <img class="card-header-title" src="@/assets/icons/draw/DrawBoard.png" alt="Drawing Board">
    </div>
  </div>
</template>

<style>
  .draw-board-card {
    display: flex;
    flex-direction: row;
    position: relative;
    justify-content: space-between;
    place-items: center;
    max-width: fit-content;
    height: fit-content;
  }

  .draw-board-card:active {
    transform: scale(0.95);
  }

  .card-header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
    width: 50%;
    height: 100%;
  }

  .draw-label {
    display: block;
    height: 100%;
    font-size: 12px;
  }

  .line {
    border: none;
    background: linear-gradient(
      rgba(255, 184, 190, 0.775),
      rgba(201, 167, 255, 0.775),
      rgba(148, 0, 141, 0.152),
      rgba(255, 173, 219, 0.775));
    content: "";
    width: 2px;
    display: block;
    height: 100%;
  }

  .card-img {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100px;
    height: 100px;
    object-fit: contain;
    object-position: center;
    opacity: 0.7;
  }

  .card-img img {
    width: 100%;
    height: 100%;
  }
</style>
