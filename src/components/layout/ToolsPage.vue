<script setup>
import DrawBoardCard from '../tools-page/draw-board/DrawBoardCard.vue';
import DrawBoard from '../tools-page/draw-board/DrawBoard.vue';
import { ref } from 'vue';

const showDrawBoard = ref(false);

</script>

<template>
  <div class="tools-page page is-active">
    <DrawBoardCard @open="showDrawBoard = true"/>
    <DrawBoard v-if="showDrawBoard" @close="showDrawBoard = false"/>
  </div>
</template>


<style scoped>
  .tools-page {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    gap: 20px;
    margin: 20px;
  }

</style>
