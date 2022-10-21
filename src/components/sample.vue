<script setup>
import { ref, computed } from 'vue'
const inputField = ref()

const dataObj = {
  a: 1,
  b: 3,
  c: 2,
  d: 4,
  e: 1,
}

const runFilter = () => {
  console.log('runFilter called')
  for (const [key, value] of Object.entries(dataObj)) {
    console.log(`${key}: ${value}`)
  }
}
const resultListFiltered = computed(() => {
  return runFilter
})
</script>

<template>
  <div>
    <input type="text" v-model="inputField" @input="runFilter">
    <ul>
      <li><span>a</span> is 1</li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
div {
  margin-top: 10vh;
}

input {
  padding: .5rem;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;

  li {
    text-align: start;
    padding: .5rem;
  }
}
</style>