<template>
  <header
    class="
      mt-2
      flex flex-row
      py-2
      px-8
      items-center
      h-14
      overflow-hidden
      justify-between
      border-b border-gray-300
      w-5/6
      xl:mx-32
    "
  >
    <div class="invisible m-4 sm:visible">
      <a>
        <img
          class="cursor-pointer"
          src="../assets/images/logo.jpg"
          height="50"
          width="50"
          alt="前端武器库"
        />
      </a>
    </div>
    <About />
  </header>
</template>

<script lang="ts">
import About from './About.vue'
import { defineComponent } from '@vue/runtime-core'
export default defineComponent({
  name: 'Header',
  components: {
    About
  }
})
</script>
