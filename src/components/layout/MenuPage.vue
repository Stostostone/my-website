<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import WelcomeCard from '@/components/menu/WelcomeCard.vue'
import WeatherCard from '@/components/menu/weather/WeatherCard.vue'
import WeatherMainCard from '@/components/menu/weather/WeatherMainCard.vue'
import TimeCard from '@/components/menu/TimeCard.vue'
import PictureCard from '@/components/menu/picture/PictureCard.vue'
import PictureDetailCard from '@/components/menu/picture/PictureDetailCard.vue'
import DisplayPicture from '../menu/DisplayPicture.vue'

const showDetailedWeather = ref(false)
const showDetailedPicture = ref(false)

</script>

<template>
  <div class="menu-page page is-active">
     <DisplayPicture/>
    <div class="menu-content">
      <WelcomeCard />
      <WeatherCard @open="showDetailedWeather = true" />
      <WeatherMainCard v-if="showDetailedWeather" @close="showDetailedWeather = false" />
      <TimeCard />
      <PictureCard @open="showDetailedPicture = true" />
      <PictureDetailCard v-if="showDetailedPicture" @close="showDetailedPicture = false" />

      <PictureCard @open="showDetailedPicture = true" />
      <PictureCard @open="showDetailedPicture = true" />
      <PictureCard @open="showDetailedPicture = true" />

    </div>
  </div>
</template>

<style scoped>
.menu-page {
  padding: 17px;
  display: flex;
  width: 100%;
  flex-direction: column;
}
.menu-content {
  display: flex;
  flex-direction: column;
  gap: 14px;
}
</style>
