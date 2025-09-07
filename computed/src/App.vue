<script setup lang="ts">
  import {ref, computed, reactive} from "vue";

  const data = reactive({
    PI: 3.14,
    radius: Math.round(Math.random() * 10)
  });
  
  const area = computed(
    (): number => data.radius * data.radius * data.PI
  );
  
  setInterval(() => {
    data.radius = Math.round(Math.random() * 10);
  }, 3000);
</script>

<template>
  <p>
    半径：{{ data.radius }} 円周率：{{ data.PI }} 面積{{ area }}
  </p>
</template>

<style scoped></style>
