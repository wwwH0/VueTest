<script setup lang="ts">
import { ref } from 'vue';

const randValue = ref("not yet!");
const onButtonClick = (): void => {
  const rand = Math.round(Math.random() * 10);
  randValue.value = String(rand);
};

const mousePointerX = ref(0);
const mousePointerY = ref(0);
const onImgMousemove = (event: MouseEvent): void => {
  mousePointerX.value = event.offsetX;
  mousePointerY.value = event.offsetY;
}

const pBgColor = ref("white");
const onPClick = (bgColor: string): void => {
  if (pBgColor.value === "white"){
    pBgColor.value = bgColor;
  }
  else {
    pBgColor.value = "white";
  }
}
</script>

<template>
  <section>
    <button v-on:click="onButtonClick">Click!!</button>
    <p>Result of the click : {{ randValue }}</p>
  </section>
  <section>
    <img src="./assets/logo.svg" alt="Vue logo" width="200" v-on:mousemove="onImgMousemove"></img>
    <p>location of pointer: x={{ mousePointerX }} y={{ mousePointerY }}</p>
  </section>
  <section>
    <p v-on:click="onPClick('red')" v-bind:style="{backgroundColor: pBgColor}">
      Change the BgColor when you click.
    </p>
  </section>
</template>

<style scoped></style>
