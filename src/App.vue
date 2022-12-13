<!-- ロジックを記述していく -->
<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import Payment from "./components/Payment.vue";
</script>

<!-- HTMLの画面要素を記述していく -->
<template>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
  <Payment />
</template>

<!-- templateに対して適用するスタイルを記述する -->
<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
