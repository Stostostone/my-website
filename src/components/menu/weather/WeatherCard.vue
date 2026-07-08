<script setup>
    import { ref } from 'vue'

    const weatherIcon = ref('@/assets/icons/weather/sunny.png');
    const weatherDesc = ref('');
    const temperature = ref(20)
    const city = ref('YongKang')
    const iconMap = {
        'Sunny': 'sunny',
        'Partly cloudy': 'cloudy',
        '阴': 'cloudy',
        'Light Rain': 'rainy',
        '雪': 'snowy',
        'Fog': 'foggy',
        '霾': 'foggy'
    };

    const emits = defineEmits(['open'])

    function getWeather() {
        fetch(`https://wttr.in/${city.value}?format=j1`, {
            method: 'GET'
        })
        .then(r => r.json())
        .then(data => {
            const desc = data.current_condition[0].weatherDesc[0].value;
            temperature.value = data.current_condition[0].temp_C;
            weatherDesc.value = desc;
            const key = Object.keys(iconMap).find(k => desc.includes(k))|| 'Sunny';
            weatherIcon.value = new URL(`/src/assets/icons/weather/${iconMap[key]}.png`, import.meta.url).href;
        });
    }
    function openWeatherMainCard() {
        emits('open');
    }
    getWeather();

</script>

<template>
    <div class="weather-card card" @click="openWeatherMainCard()">
        <div class="weather-icon">
            <img class="weather-img" :src="weatherIcon" alt="Weather">
        </div>

        <div class="weather-content">
            <p class="city">{{city}} :</p>
            <p id="weather">{{weatherDesc}} {{temperature}}°C</p>
        </div>
    </div>
</template>

<style scoped>
    .weather-card {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        position: relative;
        overflow: hidden;
        cursor: pointer;
        font-size: 17px;
    }

    .weather-icon {
        margin-right: 10px;
    }

    .weather-img {
        width: 65px;
        height: 65px;
    }

    .weather-content {
        margin-right: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }

    .weather-card::after {
        content: '';
        position: absolute;
        width: 30px;
        height: 30px;
        top: 10px;
        right: 10px;
        background: radial-gradient(circle, rgba(255, 252, 252, 0.237) 30%, transparent 70%);
        background-repeat: no-repeat;
        border-radius: 50%;
        transition: transform 0.3s ease;
        overflow: hidden;
    }

    .weather-card:active::after {
      transform: scale(50);
    }

    .weather-card:active {
        transform: scale(0.9);
    }
</style>
