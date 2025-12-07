<script setup lang="ts">
  import { ref } from "vue";

  // 5.1.1
  const inputNameModel = ref("双方向");

  // 5.1.2
  const inputNameBind = ref("しんちゃん");
  const inputNameOn = ref("ななし");
  const onInputName = (event: Event): void => {
    const element = event.target as HTMLInputElement;
    inputNameOn.value = element.value;
  }

  // 5.1.3
  const inputName2way = ref("interactive");
  const onInputName2way = (event: Event): void => {
    const element = event.target as HTMLInputElement;
    inputName2way.value = element.value;
  }
</script>

<template>
    <!-- 5.1.1 -->
  <section>
    <p>5.1.1</p>
    <input type="text" v-model="inputNameModel"></input>
    <p>{{ inputNameModel }}</p>
  </section>

  <!-- 5.1.2 -->
   <section>
    <p>5.1.2</p>
    <input type="text" v-bind:value="inputNameBind"></input>
   </section>
   <br></br>
   <section>
    <input type="text" v-on:input="onInputName"></input>
    <p>{{ inputNameOn }}</p>
   </section>

   <!-- 5.1.3 -->
    <section>
      <p>5.1.3</p>
      <input type="text" v-bind:value="inputName2way" v-on:input="onInputName2way"></input>
      <p>{{ inputName2way }}</p>
    </section>
</template>

<style scoped></style>
