<script setup lang="ts">
import { ref } from 'vue';
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';

const tweets = ref([{id: 0, description: 'Hello, World!'}, {id: 1, description: 'This is second tweet!'}])
const inputtingDescription = ref<string>('')

const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description }
  tweets.value.push(tweet);
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
  </div>
  <TweetPostForm @post-tweet="postTweet" />
    <!-- <input v-model="inputtingDescription" />
    <button class="save-button" @click="postTweet()">Post</button> -->
  <div class="tweet-container">
    <p v-if="tweets.length <= 0">No tweets have been added</p>
    <!-- <p v-show="tweets.length <= 0">No tweets have been added</p> -->
    <ul>
      <TweetList :tweets="tweets" @tweet-delete="deleteTweet" />
      <!-- <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
        <span>{{ tweet.description }}</span>
        <button class="delete-button" @click="deleteTweet(tweet.id)">DELETE</button>
      </li> -->
    </ul>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

ul {
  padding: 0;
}

input {
  margin-bottom: 16px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>
