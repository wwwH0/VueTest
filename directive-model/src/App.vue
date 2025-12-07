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

  // 5.1.4
  const inputTextarea = ref("テキストエリアへの入力文字。\n改行追加");
  const memberType = ref(1);
  const memberTypeSelect = ref(1);
  const isAgreed = ref(false);
  const isAgreed01 = ref(0);
  const selectedOS = ref([]);
  const selectedOSSelect = ref([]);
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

  <!-- 5.1.4 -->
  <p>5.1.4</p>
  <textarea v-model="inputTextarea"></textarea>
  <br></br>
  <section>
    <label><input type="radio" name="memberType" value="1" v-model="memberType"></input>通常会員</label>
    <label><input type="radio" name="memberType" value="2" v-model="memberType"></input>特別会員</label>
    <label><input type="radio" name="memberType" value="3" v-model="memberType"></input>優良会員</label>
    <br></br>
    <p>選択されたボタン：{{ memberType }}</p>
  </section>
  <br></br>
  <section>
    <select v-model="memberTypeSelect">
      <option value="1">通常会員</option>
      <option value="2">特別会員</option>
      <option value="3">優良会員</option>
    </select>
    <br></br>
    <p>選択されたリスト：{{ memberTypeSelect }}</p>
  </section>
  <br></br>
  <section>
    <label><input type="checkbox" v-model="isAgreed"></input>Agree</label>
    <p>同意の結果：{{ isAgreed }}</p>
  </section>
  <br>
  <section>
    <label><input type="checkbox" v-model="isAgreed01" true-value="1" false-value="0">Agree</label>
    <p>同意の結果：{{ isAgreed01 }}</p>
  </section>
  <br>
  <section>
    <label><input type="checkbox" v-model="selectedOS" value="1">macOS</label>
    <label><input type="checkbox" v-model="selectedOS" value="2">Windows</label>
    <label><input type="checkbox" v-model="selectedOS" value="3">Linux</label>
    <label><input type="checkbox" v-model="selectedOS" value="4">iOS</label>
    <label><input type="checkbox" v-model="selectedOS" value="5">Android</label>
    <p>選択されたOS：{{ selectedOS }}</p>
  </section>
  <br>
  <section>
    <select v-model="selectedOSSelect" multiple>
      <option value="1">macOS</option>
      <option value="2">Windows</option>
      <option value="3">Linux</option>
      <option value="4">iOS</option>
      <option value="5">Android</option>
    </select>
    <p>選択されたOS：{{ selectedOSSelect }}</p>
  </section>
</template>

<style scoped></style>
