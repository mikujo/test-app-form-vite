<script setup lang="ts">
import { ref, defineEmits, computed } from 'vue'
const inputtingDescription = ref<string>('')
const inputtingAge = ref<number>(0)

const emit = defineEmits(['post-tweet'])

const postTweet = () => {
  const tweet = {id: Math.random(), description: inputtingDescription.value, age: inputtingAge.value}
  emit('post-tweet', tweet)
  inputtingDescription.value = ''
  inputtingAge.value = 0
}

const descLenLimit = 15
const isValidDesc = computed(() => {
  if (inputtingDescription.value.length >= descLenLimit) {
    return false;
  } else {
    return true;
  }
})

const color = computed(() => {
  return isValidDesc.value ? 'white' : 'rgb(244, 194, 190)'
})

</script>

<template>
  <div class="form-container">
    <div class="form-small">
      <label>description:</label>
      <input v-model="inputtingDescription" class="input-description" />
    </div>
    <span class="err-msg" v-if="!isValidDesc"> too long description!!</span>
    <div class="form-small">
      <label>age:</label>
      <input v-model="inputtingAge" type="number" />
    </div>
    <button :disabled="!isValidDesc" class="save-button" @click="postTweet()">post</button>
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

.form-small {
  display: flex;
  margin-bottom: 8px;
}

.form-small > label {
  width: 100px;
}

.input-description {
  background-color: v-bind(color);
}

.save-button {
  color: #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
  margin-top: 12px;
}

.save-button:hover {
  background-color: #37bdbd;
}

.err-msg {
  font-weight: bold;
  color: red;
  margin-bottom: 6px;
}
</style>
