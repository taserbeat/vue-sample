<script setup lang="ts">
import { ref, reactive, computed } from "vue";

// refはプリミティブな値に対して、再レンダリングを行う対象とする
const itemName1 = ref<string>("Desk");
const itemName2 = "Bike";

// reactiveはオブジェクトなどに対して、再レンダリングを行う対象とする
const item1 = reactive({
  name: "Desk",
  price: 40000,
});

// const price1 = 40000;
const price2 = 20000;

const url1 = "https://www.amazon.co.jp/dp/B092HHW4S8";

const buy = (itemName: string) => {
  alert(`Are you sure to buy ${itemName} ?`);
};

const handleInput = (event: Event) => {
  if (!(event.target instanceof HTMLInputElement)) {
    // event引数がany型だと気持ち悪いので、きちん型付けしておく
    // https://zenn.dev/koduki/articles/0f8fcbc9a7485b
    return;
  }

  item1.name = event.target.value;
};

const clear = () => {
  item1.name = "";
  item1.price = 0;
};

const budget = 50000;

// computedで計算結果などのメモ化ができる
const priceLabel = computed(() => {
  if (item1.price > budget) return "too expensive";

  return `${item1.price}円`;
});
</script>

<template>
  <div class="container">
    <h1>Payment</h1>

    <!-- v-modelは双方向バインドで、"テキスト入力"と"リアクティブ変数の代入"のどちらでも再レンダリングされる -->
    <input v-model="item1.name" />
    <!-- この双方向バインドは次と等価な書き方である -->
    <!-- <input v-on:input="handleInput" v-bind:value="item1.name" /> -->

    <input v-model="item1.price" />

    <button v-on:click="clear">Clear</button>

    <div class="payment">
      <!-- 商品名 -->
      <label>{{ item1.name }}</label>

      <!-- 価格 -->
      <label>{{ priceLabel }}</label>

      <!-- 商品のリンク -->
      <a v-bind:href="url1">bought at ...</a>

      <!-- 購入ボタン -->
      <button v-on:click="buy(itemName1)">BUY</button>
    </div>

    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}円</label>

      <button v-on:click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 400px;
  height: 80px;
  background-color: aliceblue;
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>
