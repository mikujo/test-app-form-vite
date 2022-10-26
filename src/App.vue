<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import Payment from './components/Payment.vue'
import Tweet from './components/Tweet.vue'
import CardList from './components/CardList.vue';
import SecondCardList from './components/SecondCardList.vue';
import TodoList from './components/TodoList.vue'
import { todos, todoKey } from './useTodo'
import { ref, computed, provide } from 'vue'

// provide('todos', todos)
provide(todoKey, todos)

const currentTab = ref('')
const selectTab = (tabName: string) => {
  currentTab.value = tabName
}

const currentComponent = computed(() => {
  switch (currentTab.value) {
    case 'HelloWorld':
      return HelloWorld
    case 'Payment':
      return Payment
    case 'Tweet':
      return Tweet
    case 'CardList':
      return CardList
    case 'SecondCardList':
      return SecondCardList
    case 'TodoList':
      return TodoList
    default:
      return HelloWorld
  }
})
</script>

<template>
  <div class="tab-changer">
    <button @click="selectTab('HelloWorld')">HelloWorld</button>
    <button @click="selectTab('Payment')">Payment</button>
    <button @click="selectTab('Tweet')">Tweet</button>
    <button @click="selectTab('CardList')">CardList1</button>
    <button @click="selectTab('SecondCardList')">CardList2</button>
    <button @click="selectTab('TodoList')">TodoList</button>
  </div>
  <div class="tab-contents">
    <component :is="currentComponent"></component>
  </div>
</template>

<!-- scoped = 他のVueファイルと共有しない -->
<style scoped>
.tab-contents {
  margin-top: 20px;
}
</style>
