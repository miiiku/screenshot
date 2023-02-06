<script setup lang="ts">
import { computed, onMounted } from 'vue'
import Header from './components/Header.vue';
import Section from './components/Section.vue';

const datas = [
  {
    title: "DARKER THAN BLACK -黑之契约者-",
    images: [
      "https://qiniu.sukoshi.xyz/screenshot/darker-than-black/IMG_1070.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/darker-than-black/IMG_1071.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/darker-than-black/IMG_1078.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/darker-than-black/IMG_1079.jpeg@webp",
    ],
  },
  {
    title: "比宇宙更远的地方",
    images: [
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1335.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1338.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1339.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1343.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1348.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1351.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1355.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/farther-than-the-universe/IMG_1360.jpeg@webp",
    ],
  },
  {
    title: "野良神",
    images: [
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1174.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1207.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1209.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1176.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1208.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1201.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1205.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1203.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/noragami/IMG_1206.jpeg@webp",
    ],
  },
  {
    title: "WONDER EGG PRIORITY(奇蛋物语)",
    images: [
      "https://qiniu.sukoshi.xyz/screenshot/wonder-egg-priority/IMG_1014.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/wonder-egg-priority/IMG_1084.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/wonder-egg-priority/IMG_1083.jpeg@webp",
      "https://qiniu.sukoshi.xyz/screenshot/wonder-egg-priority/IMG_1217.jpeg@webp",
    ],
  },
  {
    title: "金色时光/青春纪行",
    images: [
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3263.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3264.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3266.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3267.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3268.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3269.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3270.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3271.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3272.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3273.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3276.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3277.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3278.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3280.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3282.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3283.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3284.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3285.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3286.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3287.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3291.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3294.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3295.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3296.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3297.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3299.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3300.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3301.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3302.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3303.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3304.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3305.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3312.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3313.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3314.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3315.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3316.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3317.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3318.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3319.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3321.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3322.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3323.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3324.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3325.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3326.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3327.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3328.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3329.jpeg",
      "https://qiniu.sukoshi.xyz/screenshot/golden-time/IMG_3330.jpeg",
    ]
  }
]

const titles = computed(() => {
  return datas.map(({ title }: { title: string }) => title);
})

onMounted(() => {
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
})
</script>

<template>
  <Header :titles="titles" />

  <Section
    v-for="(section, index) in datas"
    :key="index"
    :index="index"
    :title="section.title"
    :list="section.images"
  />
</template>

<style scoped>
</style>
