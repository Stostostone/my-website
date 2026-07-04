<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

let timer = null;
const picture = ref('');
const imagesModules = import.meta.glob('@/assets/wallpapers/*.{jpg,jpeg,png}', { eager: true, import: 'default' });
const images = Object.values(imagesModules)
const imgRef = ref(null)
const emit = defineEmits(['open'])

function getRandomImage() {
  const randomIndex = Math.floor(Math.random() * images.length);
  return images[randomIndex];
}

function switchImage() {
  imgRef.value.classList.add('fade-out')
  setTimeout(() => {
    picture.value = getRandomImage()
    requestAnimationFrame(() => {
          imgRef.value.classList.remove('fade-out')
    })
  }, 400)
}

function openDetail() {
  emit('open')
}

onMounted(() => {
  picture.value = getRandomImage();
  timer = setInterval(switchImage, 5000);
});

onUnmounted(() => {
  clearInterval(timer)
})

</script>

<template>
    <div class="picture-card card" @click="openDetail()">
        <div class="picture-image">
            <img ref="imgRef" class="picture" :src="picture" alt="Picture">

          <div class="picture-content">
              <p>stone 精选</p>
          </div>
        </div>
    </div>
</template>

<style>
  .picture-card {
  position: relative;
  padding: 0;
  aspect-ratio: 16 / 9;
  border: -2px solid rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.1);

  }

  .picture-image {
    position: relative;
    aspect-ratio: 16 / 9;
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 24px 24px 24px 24px;
  }

  .picture-image img {
    aspect-ratio: 16 / 9;
    object-fit: cover;
    object-position: center;
    width: 100%;
    height: 100%;

    animation: fadeUp 0.3s ease forwards;
    transition: opacity 0.4s ease;
    opacity: 1;
  }

  img.fade-out {
    opacity: 0;
  }

  .picture-content p {
    color:rgba(183, 80, 118, 0.77);
    font-weight: 500;
    font-size: 20px;
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 7px 14px;
    background-color: rgba(253, 253, 253, 0.099);
    width: 100%;
  }
</style>
