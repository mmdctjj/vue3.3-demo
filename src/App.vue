<script setup lang="ts">
import { ref } from 'vue';
import Child from './components/Child.vue';

export interface Command {
  msg: string
}

const count = ref(0)

const modal = ref('hello world')

const countChange = (value: any[]) => {
  console.log(value, 'countChange')
}

</script>

<template>
  <button @click="count ++">change count</button>
  <Child :msg="'hello vue3.3'" v-model="modal" :count="count" @count-change="countChange">
    default slot
    <template v-slot:item>item slot</template>
  </Child>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
