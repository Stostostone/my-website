<script setup>

  const imagesModules = import.meta.glob('../assets/wallpapers/*.{jpg,png,jpeg}', {eager:true, import:'default'})
  const images = Object.values(imagesModules)
  const emits = defineEmits(['close']);

  function closePictureDetails() {
    emits('close')
  }

</script>

<template>
  <dev class="picture-detail-card card" @click = "closePictureDetails()">
    <dev class="picture-detail grid-item" >
      <img :src="img" alt="wallpaper" v-for="(img,index) in images" :key="index">
    </dev>
    <dev class="picture-desc">

    </dev>
  </dev>
</template>

<style>

  .grid-item{
    aspect-ratio: 16 / 9;
    overflow: hidden;
    border-radius: 24px;
    grid-template-columns:repeat(auto-fill, minmax(200px, 1fr));
  }

  .grid-item img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    margin: 3px;
  }

</style>
