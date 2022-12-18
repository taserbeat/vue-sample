<script setup lang="ts">
import { ref } from "vue";

const inputDescription = ref<string>("");

const postTweet = () => {};
</script>

<template>
  <div class="form-container">
    <input v-model="inputDescription" />
    <button class="post-button" @click="postTweet()">post</button>
  </div>
</template>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

.post-button {
  color: #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.post-button:hover {
  background-color: #37bdbd;
}
</style>
