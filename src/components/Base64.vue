<template>
  <div class="flex flex-col items-center overflow-hidden justify-start">
    <Header />
    <div
      class="border w-5/6 my-4 p-4 rounded-lg flex flex-row flex-wrap bg-white"
    >
      <div class="sm:w-2/3 sm:border-r px-4">
        <div>
          <p class="text-lg">Your Text</p>
          <textarea
            class="
              shadow-md
              rounded-md
              resize-none
              text-base
              border
              hover:ring-2 hover:ring-gray-100
              py-2
              px-4
              w-full
              h-32
              mt-2
              outline-none
            "
            placeholder="Enter your text here.."
            v-model="text"
          />
        </div>
        <div>
          <p class="text-lg mt-4">Text Case</p>
          <textarea
            disabled
            class="
              shadow-md
              rounded-md
              resize-none
              text-lg
              line-clamp-4
              border
              py-2
              px-4
              w-full
              h-32
              mt-2
              bg-gray-200
            "
            >{{ isEncodeMode ? encode : decode }}</textarea
          >
        </div>
        <div class="my-8 flex sm:flex-row flex-col items-center justify-center">
          <button
            class="
              bg-gray-50
              text-green-400
              font-semibold
              w-24
              h-10
              mt-2
              sm:mr-8
              shadow-md
              border
              rounded-lg
              active:bg-gray-100
              focus:outline-none
            "
            @click="text = ''"
          >
            Clear
          </button>
          <button
            class="
              bg-green-400
              text-white
              border
              font-semibold
              w-24
              h-10
              mt-2
              sm:mr-8
              shadow-md
              rounded-lg
              active:bg-green-600
              focus:outline-none
            "
            @click="copyCode()"
          >
            Copy
          </button>
          <button
            class="
              bg-green-400
              text-white
              border
              font-semibold
              w-24
              h-10
              mt-2
              shadow-md
              rounded-lg
              active:bg-green-600
              focus:outline-none
            "
            @click="codeChange"
          >
            {{ isEncodeMode ? 'Decode' : 'Encode' }}
          </button>
        </div>
      </div>
      <div class="sm:w-1/3 p-4">
        <Statistics v-model:strs="text" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/runtime-core'
import { computed, ref } from '@vue/reactivity'
import base64 from 'base64-js'
import Header from './Header.vue'
import Footer from './Footer.vue'
import Statistics from './StatisticsVue.vue'

// 编码 string转unit8,再使用过base64.frombytearray()转成base64
const stringToUint8Array = (str: string) => {
  const arr = Array.from(str, (char) => char.charCodeAt(0))

  const tmpUint8Array = new Uint8Array(arr)
  return tmpUint8Array
}
// 解码 先使用base64.toByteArray()转成unit8，再使用该方法转成string
function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = ''
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i])
  }

  return dataString
}



export default defineComponent({
  name: 'Base64',
  components: {
    Header,
    Statistics,
    Footer
  },
  setup() {
    const text = ref('')
    const isEncodeMode = ref(true)
    const encode = computed(() => {
      return (
        base64.fromByteArray(stringToUint8Array(text.value)) ||
        'Encoded text will appear here..'
      )
    })
    const decode = computed(() => {
      try {
        return text.value
          ? Uint8ArrayToString(base64.toByteArray(text.value))
          : 'Encoded text will appear here..'
      } catch (error: any) {
        return error.message.split('.')[1]
      }
    })
    const copyCode = () => {
      navigator.clipboard.writeText(encode.value)
    }
    const codeChange = () => {
      isEncodeMode.value = !isEncodeMode.value
    }
    return {
      text,
      encode,
      copyCode,
      decode,
      codeChange,
      isEncodeMode
    }
  }
})
</script>
