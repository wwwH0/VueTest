<script setup lang="ts">
import { ref } from 'vue';

const name=ref("あいう　えおい");
</script>

<template>
  <h1>Hello!{{ name }}さん！</h1>
</template>

<style scoped></style>
