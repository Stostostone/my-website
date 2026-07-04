<script setup>
  import { ref } from 'vue'
  import WelcomeCard from '@/components/menu/WelcomeCard.vue'
  import WeatherCard from '@/components/menu/weather/WeatherCard.vue'
  import WeatherMainCard from '@/components/menu/weather/WeatherMainCard.vue';
  import TimeCard from '@/components/menu/TimeCard.vue';
  import PictureCard from '@/components/menu/picture/PictureCard.vue';
  import PictureDetailCard from '@/components/menu/picture/PictureDetailCard.vue';

  const showDetailedWeather = ref(false);
  const showDetailedPicture = ref(false)
</script>

<template>
    <div class="menu-page page is-active">
        <div class="display-picture"></div>
        <div class="menu-content">
            <WelcomeCard />
            <WeatherCard @open="showDetailedWeather = true" />
            <WeatherMainCard v-if="showDetailedWeather" @close="showDetailedWeather = false"/>
            <TimeCard />
            <PictureCard @open="showDetailedPicture = true"/>
            <PictureDetailCard v-if="showDetailedPicture" @close="showDetailedPicture = false"/>
        </div>
    </div>
</template>

<style>
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

    .display-picture {
        margin: -17px;
        width: calc(100% + 34px);
        aspect-ratio: 16 / 9;
        background: url('@/assets/backgrounds/MIKU.jpeg') no-repeat center center;
        overflow: hidden;
        background-size: cover;
        transform: translateY(-10px);
        mask-image: linear-gradient(to bottom, transparent 0%, black 3%, black 95%, transparent 100%);
        -webkit-mask-image: linear-gradient(to bottom, transparent 0%, black 3%, black 95%, transparent 100%);
        mask-size: 100% 100%;
        mask-repeat: no-repeat;
        mask-position: center;
        animation: fadeIn 2s ease;
        position: sticky;
        top: 0;
    }


</style>
