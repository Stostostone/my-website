<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const emit = defineEmits(['close'])
const canvasRef = ref(null)
const isClosing = ref(false)

let isDrawing = false
let startPoint = { x: 0, y: 0 }
let ctx = null
let canvas = null

function setupCanvas() {
  canvas = canvasRef.value
  ctx = canvas.getContext('2d')
}

function startDrawing(event) {
  isDrawing = true
  startPoint.x = event.offsetX
  startPoint.y = event.offsetY
}

function drawing(event) {
  let x = event.offsetX
  let y = event.offsetY
  if (isDrawing) {
    drawLine(startPoint.x, startPoint.y, x, y)
    startPoint.x = x
    startPoint.y = y
  }
}

function stopDrawing() {
  isDrawing = false
}

function drawLine(x1, y1, x2, y2) {
  ctx.beginPath()
  ctx.lineWidth = 2
  ctx.strokeStyle = 'black'
  ctx.moveTo(x1, y1)
  ctx.lineTo(x2, y2)
  ctx.stroke()
}

function closeDrawBoard() {
  isClosing.value = true;
  setTimeout(() => {
    emit('close')
  }, 300)
}

function clearBoard() {
  ctx.clearRect(0, 0, canvas.width, canvas.height)
}

function eraser() {
  ctx.globalCompositeOperation = 'destination-out';
  ctx.strokeStyle = 'rgba(0,0,0,1)'
}

function brush() {
  ctx.globalCompositeOperation = 'source-over';
}

onMounted(() => {
  const rect = canvasRef.value.getBoundingClientRect()
  const dpr = window.devicePixelRatio || 1
  canvasRef.value.width = rect.width * dpr
  canvasRef.value.height = rect.height * dpr

  setupCanvas()

  ctx.setTransform(dpr, 0, 0, dpr, 0, 0)
})
</script>

<template>
  <div class="overlay" :class="{'fade-out':isClosing}">
    <div class="draw-board" :class="{'fade-out':isClosing}">
      <div class="draw-board-header">
        <button class="close-button button" @click="closeDrawBoard()">
          <img src="@/assets/icons/navigation/back.png" alt="back" />
        </button>
        <h2 class="draw-board-title">Canvas 画板</h2>
      </div>
      <canvas
        id="drawing-canvas"
        @pointerdown="startDrawing"
        @pointermove="drawing"
        @pointerup="stopDrawing"
        @pointerleave="stopDrawing"
        class="drawing-canvas"
        ref="canvasRef"
      ></canvas>
      <div class="toolbar">
        <button class="draw-button button" @click="brush()">画笔</button>
        <button class="eraser-button button" @click="eraser">橡皮擦</button>
        <button class="clear-button button" @click="clearBoard()">清空</button>
        <button class="save-button button">保存</button>
      </div>
    </div>
  </div>
</template>

<style scoped>

.overlay.fade-out {
  animation: fadeOut 0.3s ease forwards;
}

.draw-board.fade-out {
  animation: fadeOut 0.3s ease forwards;
}

.draw-board {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.draw-board-header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  border-radius: 24px;
  border: none;
  padding: 10px 20px;
  background-color: rgba(255, 255, 255, 0.292);
  backdrop-filter: blur(10px);
}

.close-button {
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  height: 50px;
  width: 50px;
  cursor: pointer;
}

.close-button img {
  display: block;
  width: 24px;
  object-fit: contain;
  max-height: 24px;
}

.drawing-canvas {
  border: none;
  border-radius: 24px;
  max-height: 650px;
  width: 100%;
  height: 60vh;
  min-height: 300px;
  touch-action: none;
  background-color: rgba(255, 255, 255, 0.349);
  backdrop-filter: blur(50px);
}

.toolbar {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border-radius: 24px;
}

.button {
  animation: fadeInUp 0.3s ease var(--delay) backwards;
}

.draw-button {
  --delay:0s;
}

.eraser-button {
  --delay:0.1s;
}

.clear-button {
  --delay:0.2s;
}
.save-button {
  --delay:0.3s;
}
</style>
