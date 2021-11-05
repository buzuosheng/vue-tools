<script setup lang="ts">
const props = defineProps({
  title: String,
  desc: String,
  keywords: String,
  children: null
})
</script>

<template>
  <div class="flex flex-col items-center overflow-hidden justify-start">
    <head>
      <title>{`${{ props.title }}_前端武器库`}</title>
      <meta name="description" content="${{props.desc}}" />
      <meta name="keywords" content="${{keywords}}" />
      <meta
        name="viewport"
        content="width=device-width,initial-scale=1,maximum-scale=1"
      />
      <meta property="og:url" content="{`localhost:3000${router.saPath}`}" />
      <meta property="og:title" content="${{title}}" />
      <meta property="og:description" content="${{desc}}" />
      <meta property="og:image" content="" />
      <meta property="og:site_name" content="前端武器库" />
      <meta property="og:type" content="website" />
      <meta property="og:type" content="application" />
      <meta property="og:text" content="text" />
      <meta property="og:type" content="movie" />
    </head>
    <Header />
    {{ props.children }}
    <Footer />
  </div>
</template>
