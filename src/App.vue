<template>
  <div class="flex flex-col items-center overflow-hidden justify-start">
    <Header />
    <div
      class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 xl:mx-32 my-4 gap-4"
    >
      <Card
        title="crontab时间计算"
        desc="crontab时间测试，计算循环任务的执行时间"
        img="crontab"
      />
      <Card title="MD5编码加密" desc="使用md5算法对字符串进行加密" img="md5" />
      <Card title="摩尔斯电码" desc="将文本信息转换成摩尔斯电码" img="morse" />
      <Card
        title="base64"
        desc="将文本信息使用base64编码方式转码或者解码"
        img="base64"
      />
      <Card title="常用进制转换" desc="常用的进制转换工具" img="binary" />
      <Card title="时间戳转换" desc="时间戳在线转换" img="date" />

      <Card
        title="二维码生成器"
        desc="在线生成二维码，包括文本信息、超链接等"
        img="qrcode"
      />
      <Card title="IP地址查询" desc="在线查询IP地址信息" img="ip" />
      <Card title="代码段分享" desc="代码段生成图片分享" img="code" />
      <Card />
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/runtime-core'
import Header from './components/Header.vue'
import Card from './components/Card.vue'
import Footer from './components/Footer.vue'
export default defineComponent({
  name: 'App',
  components: {
    Header,
    Card,
    Footer
  }
})
</script>
