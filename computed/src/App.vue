<script setup lang="ts">
  import {ref, computed} from "vue";

  const radiusInit = Math.round(Math.random() * 100);
  const PI = ref(3.14);
  const radius = ref(radiusInit);
  const area = computed(
    (): number => radius.value * radius.value * PI.value
  );
  
  setInterval(() => {
    radius.value = Math.round(Math.random() * 10);
  }, 3000);
</script>

<template>
  <p>
    半径：{{ radius }} 円周率：{{ PI }} 面積{{ area }}
  </p>
</template>

<style scoped></style>
