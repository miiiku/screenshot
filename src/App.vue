<script setup lang="ts">
import { computed, onMounted, ref } from 'vue'
import Header from './components/Header.vue';
import Section from './components/Section.vue';

interface Screenshot {
  title: string,
  images: string[],
}

const dataList = ref<Array<Screenshot>>([])

const fetchList = (callback?: () => void) => {
  fetch("https://qn-wzzl.sukoshi.xyz/screenshot/screenshot.json").then(response => {
    if (response.ok) {
      return response.json();
    }
    return Promise.reject("获取数据失败")
  }).then(data => {
    dataList.value = data;
    callback && callback();
  })
  .catch(error => {
    alert(error || "网络异常");
  });
}

const initObserver = () => {
  const headerH = 60;
  const titleContainer = document.querySelector(".title-list") as HTMLElement;
  const titleEls = Array.from(document.querySelectorAll(".section-item--title"));

  if (!titleContainer) return;

  const options = {
    rootMargin: `${-headerH}px 0px 0px 0px` /** 顶部导航栏高度偏移 */,
    threshold: [0, 1] /** 只有在现实或者隐藏才触发 */,
  };

  let firstVisibleIndex = 0; /** 可见第一个标题下标 */

  const titleObserver = new IntersectionObserver(function (entries, observer) {
    entries.forEach(({ target, isIntersecting, boundingClientRect }) => {
      const elIndex = Number((target as HTMLElement).dataset?.index) || 0;
      /** 如果被触发的元素大于可见标题的第一个，那么不做任何处理 */
      if (elIndex > firstVisibleIndex) return;

      if (isIntersecting) {
        /** 往上滚动 */
        firstVisibleIndex = elIndex;
      } else if (boundingClientRect.y < headerH) {
        /** 往下滚动 */
        firstVisibleIndex = elIndex + 1;
      }
    });
    /**
     * 这里当首个可见标题下标为0 也就是默认进入页面的时候，偏移量是0%，不显示title
     * 当下标为1时，偏移量是100%，显示数据中第一个数据的title，为2时，偏移量是-200%。。。。
     */
    titleContainer.style.transform = `translate3d(0, ${firstVisibleIndex * -100}%, 0)`;
  },

  options);

  titleEls.forEach((title) => titleObserver.observe(title));
}

const titles = computed(() => {
  return dataList.value.map(({ title }: { title: string }) => title);
})

onMounted(() => {
  fetchList(() => {
    setTimeout(initObserver, 200);
  });
})
</script>

<template>
  <Header :titles="titles" />

  <Section
    v-for="(section, index) in dataList"
    :key="index"
    :index="index"
    :title="section.title"
    :list="section.images"
  />
</template>

<style scoped>
</style>
