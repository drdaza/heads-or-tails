<script lang="ts" setup>
import { ref, computed } from 'vue';
let faceCoin = ref(0);

const randomNumber = () => {
  faceCoin.value = generateRandomIntegerInRange(0, 1);
}

const restart = () => {
  faceCoin.value = 2;
}

const generateRandomIntegerInRange = (min: number, max: number) => {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

const renderResult = computed(() => {
  if (faceCoin.value == 2) return 'restart';
  return (faceCoin.value == 0) ? 'Heads' : 'Tails';
});

const showTitle = computed(() => {
  return (faceCoin.value == 0) ? 'title' : 'title-hidden';
});

const showTitle2 = computed(() => {
  return (faceCoin.value == 1) ? 'title' : 'title-hidden';
});

</script>
<template>

  <div class="coin-body">
    <p>Press in the coin for play the game and restart for play again</p>

    <button class="button-restart" @click="restart()">Restart</button>
    <div @click="randomNumber()" :class="['coin', `animate-${renderResult}`]">

      <div class="heads face"><img src="../../assets/pngwing.com (1).png" alt=""></div>
      <div class="tails face"><img src="../../assets/pngwing.com (2).png" alt=""></div>

    </div>
    <div class="result-zone">

      <h1 :class="showTitle">{{renderResult}}</h1>
      <h1 :class="showTitle2">{{renderResult}}</h1>

    </div>

  </div >
</template>
<style lang="scss" scoped>
@use '../../assets/main' as *;
.coin-body{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  p{
    margin-bottom: 2vh;
  }
  .button-restart{
    width: 40%;
    height: 5vh;
    background-color: $second-color;
    border: none;
    border-radius: 10px;
    font-size: medium;
    font-weight: bold;
  }
  .button-restart:hover{
    transition: all 0.5s ease;
    background-color: brown;
    cursor: pointer;
    color: white;
  }
  .coin {
    position: relative;
    width: 15rem;
    height: 15rem;
    margin-top: 10%;
    transform-style: preserve-3d;

    .face {
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

      img {
        width: 110%;
        height: 110%;
      }
    }

    .heads {

      background-color: burlywood;
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;

      img {
        width: 127%;
        height: 127%;
      }
    }
  }
  .result-zone{
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
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

  .title {
    animation: appear 2s;

    visibility: visible;
  }

  .title-hidden {
    animation: dissapear 2s;

    visibility: hidden;
  }

  @keyframes disappear {
    from {
      opacity: 1;

    }

    to {
      opacity: 0;

    }
  }

  @keyframes appear {
    0% {
      opacity: 0;

    }

    75% {
      opacity: 0;
    }

    to {
      opacity: 1;

    }
  }
}
</style>