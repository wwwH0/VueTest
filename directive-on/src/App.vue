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
};

const pBgColor = ref("white");
const onPClick = (bgColor: string): void => {
  if (pBgColor.value === "white"){
    pBgColor.value = bgColor;
  }
  else {
    pBgColor.value = "white";
  }
};

const pMsg = ref("Click here!");
const pBgColorEvent = ref("white");
const onPClickWithEvent = (bgcolor: string, event: MouseEvent): void => {
  pBgColorEvent.value = bgcolor;
  pMsg.value = event.timeStamp.toString();
};

const msg = ref("未送信");
const onFormSubmit = (): void => {
  msg.value = "送信されました";
};

//4.2.7
const msg4_2_7= ref("not yet!");
const onEnterKey = (): void => {
  msg4_2_7.value = "Push Enter key";
};
const onRightButtonClick = (): void => {
  msg4_2_7.value = "Right Click!!";
};
const onShiftClick = (): void => {
  msg4_2_7.value = "Push Shift key";
};
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
  <section>
    <p v-on:click="onPClickWithEvent('green', $event)" v-bind:style="{backgroundColor: pBgColorEvent}">
      {{ pMsg }}
    </p>
  </section>
  <p>4.2.6</p>
  <form action="#" v-on:submit.prevent="onFormSubmit">
    <input type="text" required></input>
    <button type="submit">Submit</button>
  </form>
  <p>{{ msg }}</p>
  <br>
  <p>4.2.7</p>
  <p>{{ msg4_2_7 }}</p>
  <input type="text" v-on:keydown.enter="onEnterKey"><br>
  <button v-on:click.right="onRightButtonClick">Right Click</button><br>
  <button v-on:click.shift="onShiftClick">Click with Shift</button>
</template>

<style scoped></style>
