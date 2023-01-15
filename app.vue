<template>
  <div ref="mainWrapper" :style="`--color: ${config?.color}`">
    <NuxtWelcome />
    {{ config }}
    <img :src="config?.logo">
  </div>
</template>
<script lang="ts" setup>
const { data: config } = await useFetch('/api/config')
const mainWrapper = ref<HTMLElement>()
useHead({
  title: config.value?.title,
  link: [
    {rel: 'icon', sizes: '192x192', type: 'image/png', href: config.value?.favicon}
  ]
})
//mainWrapper.style.setProperty('--text-color', config.color)
</script>
<style>
div {
  background-color: var(--color);
}
</style>
