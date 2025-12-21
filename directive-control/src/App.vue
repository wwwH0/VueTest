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

//6.2.3
const cocktailListInit3 = new Map<number, string>();
cocktailListInit3.set(2345, "ホワイトレディ");
cocktailListInit3.set(4412, "ブルーハワイ");
cocktailListInit3.set(6792, "ニューヨーク");
const cocktailList3 = ref(cocktailListInit3);

//6.2.4
const whiteLadyInit: {
  id: number;
  name: string;
  price: number;
  recipe: string;
} = {
  id: 2345,
  name: "ホワイトレディ",
  price: 1200,
  recipe: "ホワイトレディのレシピ～～～～～"
};
const whiteLady = ref(whiteLadyInit);

//6.2.5,6.2.6
const cocktailDataListInit = new Map<number, Cocktail>();
cocktailDataListInit.set(2345, {id: 2345, name: "ホワイトレディ", price: 1200});
cocktailDataListInit.set(4412, {id: 4412, name: "ブルーハワイ", price: 1500});
cocktailDataListInit.set(6792, {id: 6792, name: "ニューヨーク", price: 1100});
cocktailDataListInit.set(8429, {id: 8429, name: "マティーニ", price: 1500});
const cocktailDataList = ref(cocktailDataListInit);

interface Cocktail {
  id: number;
  name: string;
  price: number;
}

//6.3.1
const cocktailDataListInit2: Cocktail[] = [
  {id: 2345, name: "ホワイトレディ", price: 1200},
  {id: 4412, name: "ブルーハワイ", price: 1500},
  {id: 6792, name: "ニューヨーク", price: 1100},
  {id: 8429, name: "マティーニ", price: 1500}
];
const cocktailDataList2 = ref(cocktailDataListInit2);
const cocktail1500 = computed(
  (): Cocktail[] => {
    const newlist = cocktailDataList2.value.filter(
      (cocktailItem: Cocktail): boolean => {
        return cocktailItem.price == 1500;
      }
    );
    return newlist;
  } 
);

//6.3.2
const cocktailListInit4: string[] = ["ホワイトレディ","ブルーハワイ","ニューヨーク"];
const cocktailList4 = ref(cocktailListInit4);
const changeCocktailList = (): void => {
  cocktailList4.value = ["バラライカ", "XYZ", "マンハッタン"];
};

const addCocktailList = (): void => {
  cocktailList4.value.push("ブルームーン");
};

const deleteFromCocktailList = (): void => {
  cocktailList4.value.pop();
};

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
  <br>
  <p>6.2.3</p>
  <ul>
    <li
      v-for="[id, cocktailName] in cocktailList3"
      v-bind:key="id">
      IDが{{ id }}のカクテルは{{ cocktailName }}
    </li>
  </ul>
  <br>
  <p>6.2.4</p>
  <dl>
    <template
      v-for="(value, key) in whiteLady"
      v-bind:key="key">
      <dt>{{ key }}</dt>
      <dd>{{ value }}</dd>
    </template>
  </dl>
  <br>
  <p>6.2.5,6.2.6</p>
  <ul>
    <li
      v-for="[id, cocktailItem] in cocktailDataList"
      v-bind:key="id">
      {{ cocktailItem.name }}の値段は{{ cocktailItem.price }}円
    </li>
  </ul>
  <br>
  <p>6.2.7</p>
  <ul>
    <li
      v-for="r in 5"
      v-bind:key="r">
      半径{{ r }}の円の円周: {{ 2 * r * 3.14 }}
    </li>
  </ul>
  <br>
  <p>6.3.1</p>
  <section>
    値段が1500円のカクテルリスト
    <ul>
      <li
        v-for="cocktailItem in cocktail1500"
        v-bind:key="'cocktail1500' + cocktailItem.id">
        {{ cocktailItem.name }}の値段は{{ cocktailItem.price }}円
      </li>      
    </ul>
  </section>
  <br>
  <p>6.3.2</p>
  <ul>
    <li
      v-for="(cocktailName, index) in cocktailList4"
      v-bind:key="cocktailName">
      {{ cocktailName }}(index{{ index }})
    </li>
  </ul>
  <p>
    CocktailListを
    <button v-on:click="changeCocktailList">変更</button>
  </p>
  <p>
    CocktailListの末尾に「ブルームーン」を
    <button v-on:click="addCocktailList">追加</button>
  </p>
  <p>
    CocktailListから末尾の要素を
    <button v-on:click="deleteFromCocktailList">削除</button>
  </p>
</template>

<style scoped></style>
