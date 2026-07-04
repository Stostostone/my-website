<script setup>

  const imagesModules = import.meta.glob('@/assets/wallpapers/*.{jpg,png,jpeg}', {eager:true, import:'default'})
  const images = Object.values(imagesModules)
  const emit = defineEmits(['close']);

  function closePictureDetails() {
    emit('close')
  }

</script>

<template>
  <div class="overlay" @click.self = "closePictureDetails()">
    <div class="picture-detail-card card" >
      <div class="picture-detail grid-container" >
        <img :src="img" alt="wallpaper" v-for="(img,index) in images" :key="index">
      </div>
      <div class="picture-desc">
        <p>123</p>
      </div>
    </div>
  </div>

</template>

<style>

  .picture-detail-card.card {
    transform: none;
    max-height: fit-content;
    overflow-y: auto;
  }

  .grid-container{
    display: grid;

    grid-template-columns:repeat(auto-fill, minmax(200px, 1fr));
    gap: 5px;

  }

  .grid-container img {
    width: 100%;
    object-fit: cover;
    border-radius: 7px;
  }
</style>
