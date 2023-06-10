<template>
  <h1>{{ msg }}</h1>
  <div>{{ count }}</div>
  <slot msg="test"></slot>
  <input v-model="modelValue" />
  <slot :ids="2" name="item"></slot>
</template>
  
<script setup lang='ts'>

import { watch, watchEffect } from 'vue';
import { Command } from '../App.vue';

const { count } = defineProps<Command & { count: number}>()

const emits = defineEmits<{
  'count-change': [modelValue: number | undefined]
}>()

defineSlots<{
  default?: (props: { msg: string }) => any
  item?: (props: { ids: number }) => any
}>()

const modelValue = defineModel<string>()

watchEffect(() => {
  console.log(count, 'count')
  emits('count-change', count)
})

watch(() => modelValue.value, (val) => console.log(val))

</script>
  
<style>
  
</style>