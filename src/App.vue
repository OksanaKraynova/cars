<script setup>
import HeaderBlock from './components/HeaderBlock.vue'
import MainBlock from './components/MainBlock.vue'
import Submenu from './components/Submenu.vue'

</script>

<template>
  <div class="page">
<Submenu />
<div class='wrapper'>
  <HeaderBlock />
  <MainBlock />
</div>
  </div>

</template>

<style scoped>
  .page{
    min-height: 100vh;
    display: flex;
  }
  .wrapper{
    flex: 1;
  }
</style>
