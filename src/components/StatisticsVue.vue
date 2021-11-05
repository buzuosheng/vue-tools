<template>
  <ul class="flex flex-row flex-wrap">
    <li class="border-b text-center pb-2 mb-3 text-base w-1/2">
      <strong class="block">{{ getWords }}</strong>
      <span class="text-gray-500">Words</span>
    </li>
    <li class="border-b text-center pb-2 mb-3 text-base w-1/2">
      <strong class="block">{{ getChars }}</strong>
      <span class="text-gray-500">Characters</span>
    </li>
    <li class="border-b text-center pb-2 mb-3 text-base w-1/2">
      <strong class="block">{{ getSens }}</strong>
      <span class="text-gray-500">Sentences</span>
    </li>
    <li class="border-b text-center pb-2 mb-3 text-base w-1/2">
      <strong class="block">{{ getWspace }}</strong>
      <span class="text-gray-500">Whitespaces</span>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from '@vue/runtime-core'
const reg = /\.|\?|\!/

export default defineComponent({
  name: 'Statistics',
  props: {
    strs: {
      type: String,
      default: ''
    }
  },
  computed: {
    getWords() {
      return this.strs.split(' ').filter((x) => x.length > 0).length
    },
    getChars() {
      return this.strs.split('').length
    },
    getSens() {
      return this.strs.split(reg).length - 1
    },
    getWspace() {
      return this.strs.split(' ').length - 1
    }
  }
})
</script>
