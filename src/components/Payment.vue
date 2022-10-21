<script setup lang="ts">
import { ref, reactive, computed, watch, toRefs } from 'vue'

// const itemName = ref<string>('Desk')
// const price = 4000

const item = reactive({
  name: 'Desk',
  price: 4000
})

const budget = 50000
const priceLabel = computed(() => {
  return item.price > budget ? 'too expensive..' : item.price + 'yen'
})

const url = 'https://www.amazon.co.jp/s?k=amazon+desk&adgrpid=56967903007&gclid=CjwKCAjwwL6aBhBlEiwADycBIIkGFu-grrmXBO3_G0iMkHNCRU0zqGorbP2u7x1ku2H65_B-YynUABoC07wQAvD_BwE&hvadid=591943670794&hvdev=c&hvlocphy=1009308&hvnetw=g&hvqmt=e&hvrand=11919043611718600122&hvtargid=kwd-8591753251&hydadcr=27486_14541091&jp-ad-ap=0&tag=googhydr-22&ref=pd_sl_9gu9gyl6a7_e'
const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + '?')
}

const clear = () => {
  item.name = '',
  item.price = 0
}

</script>

<template>
  <div class="container">
    <h1>Payment!</h1>
    <input v-model="item.name" />
    <input v-model="item.price" />
    <button @click="clear">Clear</button>
    <div class="payment">
      <label>{{item.name}}</label>
      <label>{{priceLabel}}</label>
      <a :href="url">bought at...</a>
      <button @click="buy(item.name)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}

input {
  margin-bottom: 8px;
}
</style>
