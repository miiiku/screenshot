<script lang="ts" setup>
const props = defineProps<{
  title: string,
  list: string[],
  index: number,
}>()
</script>

<template>
  <section class="section-item">
    <div class="section-item--title" :data-index="index"># {{ props.title }}</div>
    <div class="section-item--screenshots">
      <div class="screenshot-block" v-for="(url, index) in props.list" :key="index">
        <img :data-src="url" :src="url" loading="lazy" :alt="props.title" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.section-item {
  padding: 20px;
}

.section-item .section-item--title {
  font-size: 28px;
  font-weight: bolder;
  margin-bottom: 20px;
}

.section-item .section-item--screenshots {
  display: grid;
  grid-template-columns: repeat(3, auto);
  gap: 12px;
}

.section-item .section-item--screenshots .screenshot-block {
  border-radius: 8px;
  padding: 8px;
  border: 1px solid #E1E1E1;
}

.section-item .section-item--screenshots .screenshot-block img {
  display: block;
  width: 100%;
  border-radius: 4px;
  object-fit: cover;
  aspect-ratio: 16/9;
}
</style>