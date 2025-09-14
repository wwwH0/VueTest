<script setup lang="ts">
import { ref } from 'vue';

const url = ref("https://vuejs.org");

const imgAttributes = ref({
  src: "/images/logo.svg",
  alt: "Vueのロゴ",
  width: 75,
  height: 75
})

const msgStyles = ref<Partial<CSSStyleDeclaration>>({
  color: "pink",
  fontSize: "20pt",
  backgroundColor: "black"
})
</script>

<template>
  <p><a v-bind:href="url" target="_blank">Vue.js Site</a></p>
  <p><a :href="url" target="_blank">Vue.js Site 省略系</a></p>
  <p><a v-bind:href="url + '/guide/introduction.html'" target="_blank">Vue.js Guide</a></p>
  <!-- <p><button type="button" v-bind:disabled="isSendButtonDisabled">送信</button></p> -->

  <p v-bind:style="msgStyles">スタイルテスト</p>

  <p><img v-bind="imgAttributes"></img></p>
  <p><img v-bind="imgAttributes" title="logo_title!"></img></p>
  <p><img v-bind="imgAttributes" alt="logo_alt!"></img></p>
  <p><img alt="VueLogo" src="./assets/logo.svg" ></p>

</template>

<style scoped></style>