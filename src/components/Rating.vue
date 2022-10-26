<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps(['modelValue'])
const emits = defineEmits(['update:modelValue'])

const isActiveBtn = ref<string>(props.modelValue)
const onClick = (btnType: string) => {
  isActiveBtn.value = btnType
  emits('update:modelValue', isActiveBtn.value)
}

</script>

<template>
  <ul>
    <li>
      <button type="button" :class="{active: isActiveBtn === 'bad'}" @click="onClick('bad')">Bad</button>
    </li>
    <li>
      <button type="button" :class="{active: isActiveBtn === 'average'}" @click="onClick('average')">Average</button>
    </li>
    <li>
      <button type="button" :class="{active: isActiveBtn === 'great'}" @click="onClick('great')">Great</button>
    </li>
  </ul>
</template>

<style scoped>
.active {
  color: rgb(216, 88, 110);
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid gray;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>
