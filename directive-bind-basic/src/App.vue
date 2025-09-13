`<script setup lang="ts">
import { ref } from 'vue';

const url = ref("https://vuejs.org");
const isSendButtonDisabled = ref(true);
const widthOrHeight = ref("height");
const widthOrHeightValue = ref(100);
</script>

<template>
  <p><a v-bind:href="url" target="_blank">Vue.js Site</a></p>
  <p><a :href="url" target="_blank">Vue.js Site 省略系</a></p>
  <p><a v-bind:href="url + '/guide/introduction.html'" target="_blank">Vue.js Guide</a></p>
  <p><button type="button" v-bind:disabled="isSendButtonDisabled">送信</button></p>

  <p><img alt="VueLogo" src="./assets/logo.svg" v-bind:[widthOrHeight]="widthOrHeightValue"></p>

</template>

<style scoped></style>
`