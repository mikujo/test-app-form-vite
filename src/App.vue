<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import PyamentVue from './components/Payment.vue'
import Tweet from './components/Tweet.vue'
</script>

<template>
  <Tweet />
  <!-- <PyamentVue /> -->
  <!-- <HelloWorld msg="Vite + Vue + typescript" /> -->
</template>

<!-- scoped = 他のVueファイルと共有しない -->
<style scoped>
</style>
