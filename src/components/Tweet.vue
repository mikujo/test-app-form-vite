<script setup lang="ts">
import { ref, Ref } from 'vue'
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';

export type Tweet = {
  id: number,
  description: string,
  age: number,
}

const tweets: Ref<Tweet[]> = ref([{id: 0, description: 'Hello world', age: 24}, {id: 1, description: 'this is the second', age: 18}])

const postTweet = (tweet: Tweet) => {
  tweets.value.push(tweet)
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">No tweets have been added</p>
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
</style>
