<script setup lang="ts">
  import { defineProps, defineEmits } from 'vue';
  type Tweet = {
    id: number,
    description: string,
  }

  type Props = {
    tweets: Tweet[]
    deleteTweet: (id: number) => void
  }
  
  defineProps<Props>()

//   const emit = defineEmits(['tweet-delete'])

//   const deleteTweet = (id: number) => {
//     emit('tweet-delete', id)
//   }

</script>

<template>
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">DELETE</button>
  </li>
</template>

<style scoped>
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

.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: rgb(194, 187, 139);
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.delete-button:hover {
  background-color: rgb(145, 129, 6);
}
</style>
