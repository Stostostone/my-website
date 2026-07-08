<script setup>
  import { ref, onMounted } from 'vue'
  const suggestion = ref('Have a nice day!');

  function updateSuggestion() {
    const hour = new Date().getHours();
    if (hour < 12) {
      suggestion.value = 'Good morning! Have a nice day ahead!';
    } else if (hour < 18) {
      suggestion.value = 'Good afternoon! Keep up the good work!';
    } else if (hour < 22) {
      suggestion.value = 'Good evening! Relax and unwind!';
    } else {
      suggestion.value = "It's time to go to bed! ";
    }
  }

  function updateTime() {
    const timeElement = document.getElementById('time');
    const dateElement = document.getElementById('date');
    if (timeElement && dateElement) {
      timeElement.textContent = new Date().toLocaleTimeString();
      dateElement.textContent = new Date().toLocaleDateString();
    }
  }

  onMounted(() => {
    updateSuggestion();
    updateTime();
    setInterval(updateTime, 1000);
  });
</script>

<template>
  <div class="time-card card">
    <div class="clock">
        <p id="time">{{ new Date().toLocaleTimeString() }}</p>
        <p id="date">{{ new Date().toLocaleDateString() }}</p>
    </div>
      <div class="time-content label">
        <p>{{ suggestion }}</p>
      </div>
  </div>
</template>

<style scoped>
  .time-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    color: #fff;
    text-align: center;
  }

  .clock {
    font-size: 17px;
  }

  .time-content {
    font-size: 17px;
  }

  .time-content{
    display: flex;
    margin: 0 0;
    background-color: rgba(79, 0, 0, 0.05);
    border: 1px solid rgba(65, 0, 0, 0.15);
  }
</style>
