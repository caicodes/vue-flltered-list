<script setup>
import { ref, computed } from 'vue'

const inputField = ref()
let resultList = {}
const dataObj = {
  a: 1,
  b: 3,
  c: 2,
  d: 4,
  e: 1,
}

function runFilter() {
  resultList = {}
  for (const [key, value] of Object.entries(dataObj)) {
    if (!inputField.value) {
      resultList[key] = value
    } else {
      if (inputField.value == value) {
        resultList[key] = value
      }
    }
  }
  return resultList
}

const resultListFiltered = computed(() => {
  runFilter()
  return resultList
})


</script>

<template>
  <div>
    <input type="text" id="inputField" v-model="inputField" @input="runFilter">
    <TransitionGroup name="list" tag="ul">
      <li v-for="(value,key) in resultListFiltered" :key="key"
        :class="{ red: (value < 2), blue: (value > 2), gray: (value == 2) }"><span>{{key}}</span> is {{value}}</li>
    </TransitionGroup>
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

    span {
      text-transform: uppecase;
    }

    &.red {
      color: palevioletred;
    }

    &.blue {
      color: lightblue;
    }

    &.gray {
      color: gray;
    }
  }
}

// transitions
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
  position: absolute;
}
</style>