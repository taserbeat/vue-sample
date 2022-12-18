<script setup lang="ts">
import { ref } from "vue";
import TweetPostForm from "./TweetPostForm.vue";
import TweetList from "./TweetList.vue";

const tweets = ref([
  { id: 0, description: "Hello World!" },
  { id: 1, description: "This is 2nd tweet!" },
]);

const postTweet = (description: string) => {
  const tweet = {
    id: tweets.value.length,
    description: description,
  };

  tweets.value.push(tweet);
};

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((tweet) => tweet.id !== id);
};
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>

    <div class="form-container">
      <!-- 52. 子コンポーネントから親コンポーネントにイベントを通知する -->
      <TweetPostForm @post-tweet="postTweet" />
    </div>

    <div class="tweet-container">
      <!-- tweetsの要素が0個の場合はメッセージを表示する -->
      <!-- 条件付きレンダリングは、v-ifまたはv-showというディレクティブを使用する -->
      <p v-if="tweets.length === 0">Tweets does not exist</p>
      <!-- <p v-show="tweets.length === 0">Tweets does not exist</p> -->

      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet" />
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
</style>
