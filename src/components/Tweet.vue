<script setup lang="ts">
import { ref } from "vue";

const tweets = ref([
  { id: 0, description: "Hello World!" },
  { id: 1, description: "This is 2nd tweet!" },
]);

const inputDescription = ref<string>("");

const postTweet = () => {
  const tweet = {
    id: tweets.value.length,
    description: inputDescription.value,
  };

  tweets.value.push(tweet);

  inputDescription.value = "";
};

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((tweet) => tweet.id !== id);
};
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>

    <div class="form-container">
      <input v-model="inputDescription" />
      <button class="post-button" @click="postTweet()">post</button>
    </div>

    <div class="tweet-container">
      <!-- tweetsの要素が0個の場合はメッセージを表示する -->
      <!-- 条件付きレンダリングは、v-ifまたはv-showというディレクティブを使用する -->
      <p v-if="tweets.length === 0">Tweets does not exist</p>
      <!-- <p v-show="tweets.length === 0">Tweets does not exist</p> -->

      <ul>
        <li class="tweet-list" v-for="tweet in tweets" :key="tweet.id">
          <span>{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">
            delete
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

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

.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: rgb(204, 219, 233);
  padding: 8px 20px;
  width: 300px;
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

.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: #c99a68;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.delete-button:hover {
  background-color: #ac783f;
}

input {
  margin-bottom: 16px;
}
</style>
