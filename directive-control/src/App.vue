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

//6.2.1
const cocktailListInit: string[] = ["ホワイトレディ","ブルーハワイ","ニューヨーク"];
const cocktailList = ref(cocktailListInit);

//6.2.2
const cocktailListInit2: {[key: number]: string;} = {
  2345: "ホワイトレディ",
  4412: "ブルーハワイ",
  6792: "ニューヨーク"
};
const cocktailList2 = ref(cocktailListInit2);

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
  <br>
  <p>6.1.4</p>
  <section>
    "v-if"
    <p v-if="showOrNot">
      合致
    </p>
  </section>
  <section>
    "v-show"
    <p v-show="showOrNot">
      合致
    </p>
  </section>
  <br>
  <p>6.2.1</p>
  <ul>
    <li
      v-for="cocktailName in cocktailList"
      v-bind:key="cocktailName">
      {{ cocktailName }}
    </li>
  </ul>
  <ul>
    <li
      v-for="(cocktailName, index) in cocktailList"
      v-bind:key="cocktailName">
      {{ cocktailName }}(index:{{ index }})
    </li>
  </ul>
  <br>
  <p>6.2.2</p>
  <ul>
    <li
      v-for="(cocktailName, id) in cocktailList2"
      v-bind:key="'cocktailList2' + id">
      IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>
  <ul>
    <li
      v-for="(cocktailName, id, index) in cocktailList2"
      v-bind:key="'cocktailList2WithIndex' + id">
      {{ index + 1 }}:IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>
</template>

<style scoped></style>
