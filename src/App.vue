<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    
      <h1>HI! this is a head or tails game</h1>
    
  </header>

  <RouterView />
</template>

<style lang="scss" scoped>
header{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 20vh;
}
</style>
