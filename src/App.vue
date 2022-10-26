<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import PyamentVue from './components/Payment.vue'
import Tweet from './components/Tweet.vue'
import CardList from './components/CardList.vue';
import SecondCardList from './components/SecondCardList.vue';
import { ref, computed } from 'vue'

const currentTab = ref('')
const updateTab = (tabName: string) => {
  currentTab.value = tabName
}

const currentComponent = computed(() => {
  switch (currentTab.value) {
    case 'CardList':
      return CardList
    case 'SecondCardList':
      return SecondCardList
    default:
      return CardList
  }
})
</script>

<template>
  <div class="tab-changer">
    <button @click="updateTab('CardList')">Tab 1</button>
    <button @click="updateTab('SecondCardList')">Tab 2</button>
  </div>
  <div class="tab-contents">
    <component :is="currentComponent"></component>
    <!-- <CardList v-if="isFirstTab"></CardList>
    <SecondCardList v-if="!isFirstTab"></SecondCardList> -->
  </div>
  <!-- <Tweet /> -->
  <!-- <PyamentVue /> -->
  <!-- <HelloWorld msg="Vite + Vue + typescript" /> -->
</template>

<!-- scoped = 他のVueファイルと共有しない -->
<style scoped>
.tab-contents {
  margin-top: 20px;
}
</style>
