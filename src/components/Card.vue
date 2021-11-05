<template>
  <a>
    <div
      class="
        shadow-sm
        hover:shadow-md
        flex flex-col
        p-2
        font-mono
        border
        cursor-pointer
        no-underline
        transform
        hover:scale-105
        transition-transform
        duration-300
        border-gray-400
        rounded-lg
        h-32
        w-80
      "
    >
      <div
        class="
          flex flex-row
          justify-between
          items-center
          border-b border-gray-300
          py-2
          px-5
          mb-2
        "
      >
        <img
          :src="`/src/assets/images/${img}.jpg`"
          :alt="title"
          height="40"
          width="40"
        />
        <h3>{{ title }}</h3>
      </div>
      <div class="text-sm h-10 line-clamp-2 text-gray-500 px-2">
        {{ desc }}
      </div>
    </div>
  </a>
</template>

<script lang="ts">
import { defineComponent } from '@vue/runtime-core'
import { toRefs } from 'vue'

interface CardProps {
  title: string
  img: string
  desc: string
}

export default defineComponent({
  name: 'Card',
  props: ['title', 'img', 'desc'],
  // {
  //   title: { type: String, default: 'Default title' },
  //   img: {
  //     type: String,
  //     default: 'Default image'
  //   },
  //   desc: {
  //     type: String,
  //     default: 'Default description'
  //   }
  // },
  setup(props: CardProps) {
    let { title, img, desc } = toRefs(props)
    return {
      title,
      img,
      desc
    }
  }
})
</script>
