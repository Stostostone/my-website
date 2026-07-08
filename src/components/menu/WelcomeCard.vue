<script setup>
import { ref } from 'vue'

</script>
<template>
  <div class="welcome-card card">
    <div class="welcome-content">
      <h2>欢迎来到石头屋!</h2>
      <p>Stone House</p>
      <div class="labels">
        <label class="label">vue</label>
        <label class="label">javascript</label>
      </div>
    </div>
    <div class="nav-link-button">
      <a class="link-button" href="https://github.com/Stostostone" target="_blank" rel="noopener noreferrer">
        <img src="@/assets/icons/link/github.png" alt="Github" />
      </a>
      <a class="link-button" href="mailto:lowlystone@gmail.com" target="_blank" rel="noopener noreferrer">
        <img src="@/assets/icons/link/email.png" alt="Email" />
      </a>
      <a
        class="link-button"
        href="https://space.bilibili.com/440117109?spm_id_from=333.1007.0.0"
        target="_blank"
        rel="noopener noreferrer"
      >
        <img src="@/assets/icons/link/bilibili.png" alt="Bilibili" />
      </a>
      <a
        class="link-button"
        href="https://store.steampowered.com"
        target="_blank"
        rel="noopener noreferrer"
      >
        <img src="@/assets/icons/link/steam.png" alt="Steam" />
      </a>
    </div>
  </div>
</template>

<style scoped>
p {
  padding: 4px 0;
}
.welcome-card {
  max-height: fit-content;
  gap: 14px;
}
.nav-link-button {
  display: flex;
  justify-content: right;
  align-items: right;
  gap: 14px;
  flex-direction: row;
  margin-top: auto;
}
.welcome-content h2 {
  position: relative;
}

.welcome-content h2::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 1px;
  width: 100%;
  overflow: hidden;
  background: #72013d4e;
}

.labels {
  display: flex;
  flex-direction: row;
  gap: 4px;
}

.label {
  background-color: rgba(193, 57, 57, 0.121);
  border: none;
  transform: translateY(5px);
  padding: 1px 4px 1px 4px;
  font-size: 14px;
}
</style>
