<script setup>
import { ref } from 'vue'

const github = ref('https://github.com')
const email = ref('example@example.com')
const bilibili = ref('https://www.bilibili.com')
const steam = ref("https://store.steampowered.com")

</script>
<template>
    <div class = "welcome-card card">
        <div class="welcome-content">
            <h2>欢迎来到石头屋!</h2>
            <p>卑微石头手搓的小屋</p>
            <p class="lable">Stone house</p>
        </div>
        <div class = "nav-link-button">
            <a class="link-button" href= ${github} target="_blank" rel="noopener noreferrer">
                <img src="@/assets/icons/link/github.png" alt="Github">
            </a>
            <a class="link-button" href="https://email.com" target="_blank" rel="noopener noreferrer">
                <img src="@/assets/icons/link/email.png" alt="Email">
            </a>
            <a class="link-button" href="https://www.bilibili.com" target="_blank" rel="noopener noreferrer">
                <img src="@/assets/icons/link/bilibili.png" alt="Bilibili">
            </a>
            <a class="link-button" href="https://store.steampowered.com" target="_blank" rel="noopener noreferrer">
                <img src="@/assets/icons/link/steam.png" alt="Steam">
            </a>
        </div>
    </div>
</template>

<style>
    p {
        padding: 4px 0;
    }
    .welcome-card{
        max-height: fit-content;
        gap: 14px;
    }
    .nav-link-button{
        display: flex;
        justify-content: right;
        align-items: right;
        gap: 14px;
        flex-direction: row;
        margin-top: auto;
    }
    .welcome-content h2{
        position: relative;
    }

    .welcome-content h2::after{
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
    .lable {
        transform: translateY(5px);
        padding: 2px 14px 2px 14px;
    }

</style>
