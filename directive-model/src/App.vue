<script setup lang="ts">
  import { ref } from "vue";

  // 5.1.1
  const inputNameModel = ref("双方向");
</script>

<template>
    <!-- 5.1.1 -->
  <section>
    <input type="text" v-model="inputNameModel"></input>
    <p>{{ inputNameModel }}</p>
  </section>
</template>

<style scoped></style>
