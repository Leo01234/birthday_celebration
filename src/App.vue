<script setup>
import BirthdayCake from './components/BirthdayCake.vue'
import CelebrationAnimation from './components/CelebrationAnimation.vue'
</script>

<template>
  <h1 class="title">祝槐序生日快乐</h1>
  <BirthdayCake />
  <CelebrationAnimation />
</template>

<style scoped>
  .title {
    position: absolute;
    width: 100%;
    text-align: center;
    font-weight: bold;
    font-size: 64px;
    background: -webkit-linear-gradient(90deg, #e87887 50%, #ff64e5);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
</style>
