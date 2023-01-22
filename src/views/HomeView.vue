<script setup lang="ts">
import Coin from '@/components/CoinComponent/Coin.vue';
</script>

<template>
  <main>
    <Coin/>
  </main>
</template>
<style lang="scss" scoped>
  main{
      width: 100%;
      height: 80vh;
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
  }
</style>