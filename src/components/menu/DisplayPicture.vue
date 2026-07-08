<script>
import {ref, onMounted, onUnmounted} from 'vue'

const displayPicture = ref(null)

// onMounted(() => {
//   const img = displayPicture.value

//   window.addEventListener('scroll', () => {
//     const rect = img.getBoundingClientRect()
//     const progress = Math.max(0, Math.min(1, 1 - (rect.top - 962) / window.innerHeight))
//     img.style.opacity = progress
//   })
// })

// onUnmounted(() => {
//   removeEventListener()
// })

</script>

<template>
    <div class="display-picture" ref="displayPicture"></div>
</template>

<style scoped>
.display-picture {
  margin: -17px;
  width: calc(100% + 34px);
  aspect-ratio: 16 / 9;
  background: url('@/assets/backgrounds/MIKU.jpeg') no-repeat center center;
  overflow: hidden;
  background-size: cover;
  transform: translateY(-10px);
  mask-image: linear-gradient(to bottom, transparent 0%, black 3%, black 95%, transparent 100%);
  -webkit-mask-image: linear-gradient(
    to bottom,
    transparent 0%,
    black 3%,
    black 95%,
    transparent 100%
  );
  mask-size: 100% 100%;
  mask-repeat: no-repeat;
  mask-position: center;
  animation: fadeIn 2s ease;

  position: sticky;
  top: 0;
}
</style>
