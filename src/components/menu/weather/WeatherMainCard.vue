<script setup>
    import { ref, onMounted, onUnmounted } from 'vue'
    import * as echarts from 'echarts'

    const city = ref('永康')
    const inputCity = ref()
    const daytemp = ref([null, null, null, null, null, null, null])
    // const descriptions = ref([null, null, null, null, null, null, null])
    const chartRef = ref(null)
    let myChart = null

    const emits = defineEmits(['close'])
    const isClosing = ref(false)


    function searchWeather() {
        // Function to search for weather information

        if (inputCity.value) {
            city.value = inputCity.value
        }
        else {
            city.value = '永康'
        }
        console.log(`Searching weather for ${city.value}`)
        fetch (`https://wttr.in/${city.value}?format=j1`)
            .then(response => response.json())
            .then(data => {
                console.log(data)
                const days = data.weather.length;
                for (let i = 0; i < days; i++) {
                  daytemp.value[i] = data.weather[i].maxtempC;
                  // descriptions.value[i] = data.weather[i].weatherDesc[0].value;
                }
                updateChart();
                inputCity.value = '';
            })
    }

    onMounted(() => {
      myChart = echarts.init(chartRef.value)

      const option = {
        xAxis: {
          type: 'category',
          data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
        },
        yAxis: {
          type: 'value'
        },
        series: [{
          data: daytemp.value,
          type: 'line'
        }]
      };

      myChart.setOption(option);

      searchWeather(); // Fetch weather data for the default city
      updateChart(); // Update the chart with the fetched data
    })

    onUnmounted(() => {
      if (myChart) {
        myChart.dispose();
      }
    })

    function updateChart() {
      if (myChart) {
        myChart.setOption({
          series: [{
            data: daytemp.value
          }]
        });
      }
    }

    function closeCard() {
      isClosing.value = true;
      setTimeout(() => {
        emits('close');
      }, 300); // Match the duration of the fade-out animation
    }
</script>

<template>
  <div class="overlay" @click.self="closeCard()" :class="{'fade-out': isClosing}">
    <div class="weather-main-card card" @click.stop :class="{ 'fade-out': isClosing }">
      <div class="search-weather-card">
        <button class="search-button button" @click="searchWeather">搜索</button>
        <input type="text" v-model="inputCity" placeholder="输入城市名称" @keyup.enter="searchWeather">
      </div>
      <div class="weather-display">
          <h3>{{city }}气温:</h3>
        <div ref="chartRef" style="width: 350px; height: 400px;" >
        </div>
      </div>
    </div>
  </div>

</template>

<style scroped>
  .weather-main-card {
    position: relative;

  }

  /* .overlay {
    position: fixed;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(20px);
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    z-index: 100;
    inset: 0;
    animation: fadeIn 0.3s ease;
  }

  .overlay.fade-out {
    animation: fadeOut 0.3s ease 0.2s forwards;
  } */

  .weather-main-card.fade-out {
    animation: fadeOutDown 0.2s ease forwards;
  }

  .search-weather-card {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px 30px;
    flex-direction: row;
    background-color: transparent;
    max-width: fit-content;
    max-height: fit-content;
    gap: 10px;

  }

  input {
    border: 1px solid rgba(255, 255, 255, 0.184);
    background-color: rgba(255, 255, 255, 0.3);
    color: rgba(160, 160, 160, 0.8);
    padding: 3px 10px;
    border-radius: 24px;
    transition: transform 0.2s ease;
  }

  input:focus {
    outline: rgba(123, 123, 123, 0.3) solid 2px;
    transform: scale(1.03);
  }


</style>


