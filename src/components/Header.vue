<script lang="ts" setup>
defineProps<{
  titles: string[]
}>()
</script>

<template>
  <header class="header-container">
    <div class="header-title h-20 flex items-center">
      <h1 class="tracking-[1rem] font-bold text-sm md:text-lg lg:text-2xl xl:text-4xl">SCREENSHOT</h1>
    </div>
    <div class="header-img h-16 flex items-center">
      <svg class="h-10 w-10  md:h-12 lg:h-16 xl:h-16 md:w-12 lg:w-16 xl:w-16" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg">
        <path d="M418.7136 797.0816H287.3344c-42.24 0-76.4928-34.2528-76.4928-76.4928V211.9168h207.872v585.1648z" fill="#ffa115"></path>
        <path d="M930.5088 777.8304H872.96V289.1264c0-62.1056-50.5344-112.64-112.64-112.64H223.9488V113.1008c0-16.9472-13.7728-30.72-30.72-30.72s-30.72 13.7728-30.72 30.72v63.3856H95.1808c-16.9472 0-30.72 13.7728-30.72 30.72s13.7728 30.72 30.72 30.72h67.328v488.704c0 62.1056 50.5344 112.64 112.64 112.64H811.52v69.2736c0 16.9472 13.7728 30.72 30.72 30.72s30.72-13.7728 30.72-30.72v-69.2736h57.4976c16.9472 0 30.72-13.7728 30.72-30.72s-13.7216-30.72-30.6688-30.72z m-655.36 0c-28.2112 0-51.2-22.9888-51.2-51.2V237.9264H760.32c28.2112 0 51.2 22.9888 51.2 51.2v488.704H275.1488z" fill="#474A54"></path>
        <path d="M693.248 513.4336c-16.9472 0-30.72 13.7728-30.72 30.72v147.712c0 16.9472 13.7728 30.72 30.72 30.72s30.72-13.7728 30.72-30.72v-147.712c0-16.9984-13.7728-30.72-30.72-30.72z" fill="#474A54"></path>
      </svg>
    </div>
    <div class="header-sticky">
      <ul class="title-list">
        <li class="title-list--item">O v O</li>
        <li class="title-list--item" v-for="(title, index) in titles" :key="index">{{ title }}</li>
      </ul>
    </div>
  </header>
</template>

<style scoped>
.header-container {
  position: sticky;
  top: -182px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 280px;
}

.header-container .header-sticky {
  width: 100%;
  height: 60px;
  overflow: hidden;
  text-align: center;
  background-color: #ffffff;
}

.header-container .header-sticky .title-list {
  width: 100%;
  height: 100%;
  transform: translate3d(0, 0, 0);
  transition: transform 0.3s ease;
}

.header-container .header-sticky .title-list .title-list--item {
  height: 60px;
  line-height: 60px;
  font-weight: bolder;
}
</style>