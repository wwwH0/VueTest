<script setup lang="ts">
  import {computed, ref} from "vue";

//6.1.1
const number =ref(80);
const showOrNot = computed(
  (): boolean => {
    let showOrNot = false;
    const rand = Math.round(Math.random() * 100);
    if(rand >= 50){
      showOrNot = true;
    }
    return showOrNot;
  }
);

//6.1.2,6.1.3
const randomNumber = computed (
  (): number => {
    return Math.round(Math.random() * 100);
  }
);
</script>

<template>
  <p>6.1.1</p>
  <p v-if="number >= 50">
    条件に合致したので表示1️⃣
  </p>
  <p v-if="Math.round(Math.random() * 100) >= 50">
    条件に合致したので表示2️⃣
  </p>
  <p v-if="showOrNot">
    条件に合致したので表示3️⃣
  </p>
  <br>
  <p>6.1.2</p>
  <p>
    点数は{{ randomNumber }}点で
    <span v-if="randomNumber >= 80">優です。</span>
    <span v-else-if="randomNumber >= 70">良です。</span>
    <span v-else-if="randomNumber >= 60">可です。</span>
    <span v-else>不可です。</span>
  </p>
  <br>
  <p>6.1.3</p>
  <p>
    点数は{{ randomNumber }}点で
    <template v-if="randomNumber >= 80">
      優です。
      <span style="color: red;">すばらしい！</span>
    </template>
    <span v-else-if="randomNumber >= 70">良です。</span>
    <span v-else-if="randomNumber >= 60">可です。</span>
    <span v-else>不可です。</span>
  </p>
</template>

<style scoped></style>
