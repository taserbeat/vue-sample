<script setup lang="ts">
const itemName1 = "Desk";
const itemName2 = "Bike";

const price1 = 40000;
const price2 = 20000;

const url1 = "https://www.amazon.co.jp/dp/B092HHW4S8";

const buy = (itemName: string) => {
  alert(`Are you sure to buy ${itemName} ?`);
};
</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <div class="payment">
      <!-- 商品名 -->
      <label>{{ itemName1 }}</label>

      <!-- 価格 -->
      <label>{{ price1 }}円</label>

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