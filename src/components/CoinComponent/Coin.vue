<script lang="ts" setup>
import { ref, computed } from 'vue';
let faceCoin = ref(0);

const randomNumber = ()=>{
    faceCoin.value = generateRandomIntegerInRange(0,1);
    
}
const generateRandomIntegerInRange = (min :number, max:number)=>{
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
const renderResult = computed(()=>{
   return (faceCoin.value==0) ? 'Heads': 'Tails';
})

const showTitle = computed(()=>{
  return (faceCoin.value==0)? 'title' : 'title-hidden';
})
const showTitle2 = computed(()=>{
  return (faceCoin.value==1)? 'title' : 'title-hidden';
})

</script>
<template>
    <div @click="randomNumber()" :class="['coin', `animate-${renderResult}`]">
        <div class="heads face"><h1 :class="showTitle">{{renderResult}}</h1></div>
        <div class="tails face"><h1 :class="showTitle2">{{renderResult}}</h1></div>
        
    </div>
    
    
</template>
<style lang="scss" scoped>
.coin {
  position: relative;
  width: 15rem;
  height: 15rem;

  transform-style: preserve-3d;
  .face{
  width: 100%;
  height: 100%;
  border: 2px solid black;
  border-radius: 50%;
  backface-visibility: hidden;
  background-size: contain;
  position: absolute;
  }
  .tails {
    background-color: burlywood;
    transform: rotateX(-180deg);
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  .heads {
    
    background-color: cadetblue;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;

  }
}

.animate-Heads {
  animation: flipHeads 2s;
  animation-fill-mode: forwards;
}
@keyframes flipHeads {
  from {
    transform: rotateX(0deg);
  }
  to {
    transform: rotateX(1800deg);
  }
}



.animate-Tails {
  animation: flipTails 2s;
  animation-fill-mode: forwards;
}

@keyframes flipTails {
  from {
    transform: rotateX(0deg);
  }
  to {
    transform: rotateX(1620deg);
  }
}
.title{
  animation: appear 2s;

  visibility: visible;
}
.title-hidden{
  animation: dissapear 2s;

  visibility: hidden;
}
@keyframes disappear {
  from{
   opacity: 1;
    
  }
  to{
   opacity: 0;
    
  }
}
@keyframes appear {
  0%{
    opacity: 0;
    
  }
  75%{
    opacity: 0;
  }
  to{
    opacity: 1;
    
  }
}
</style>