<script lang="ts" setup>
const props = defineProps<{
  title: string,
  list: string[],
  index: number,
}>()
</script>

<template>
  <section class="section-item p-5">
    <div class="section-item--title mb-5 font-bold text-lg md:text-lg lg:text-xl xl:text-2xl" :data-index="index"># {{ props.title }}</div>
    <div class="section-item--screenshots grid gap-3 grid-cols-2 md:grid-cols-3 xl:grid-cols-4">
      <div class="screenshot-block rounded-lg p-2 border border-gray-300" v-for="(url, index) in props.list" :key="index">
        <img class="block rounded object-cover aspect-video" :data-src="url" :src="url" loading="lazy" :alt="props.title" />
      </div>
    </div>
  </section>
</template>