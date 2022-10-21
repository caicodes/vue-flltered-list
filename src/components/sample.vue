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

  Object.assign(resultListFiltered, dataObj)

}
const resultListFiltered = computed(() => {
  return runFilter
})
</script>

<template>
  <input type="text" v-model="inputField" @input="runFilter">
  <ul>
    <li><span>a</span> is 1</li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
}
</style>