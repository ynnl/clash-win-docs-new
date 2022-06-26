<template>
  <div class="list">
    <div v-for="(ad, index) in ads" :key="ad.url">
      <lazy-img :src="ad.img" class="item" @click="handleAdClick(ad)" />
      <div v-if="index < ads.length - 1" class="saperator"></div>
    </div>
  </div>
</template>

<script>
import LazyImg from "./lazy-img.vue";

export default {
  components: { LazyImg },
  data() {
    return {
      ads: [
        {
          url: "https://i.sw8.pw/E6wn",
          img: "https://www.live4yc.top/public/static/upload/images/goods/2022/01/29/suwa.gif",
        },
        {
          url: "https://fastlink.so/auth/register?code=clashw",
          img: "https://download.fastlink.digital/fastlink_banner.jpg",
        },
      ],
    };
  },
  methods: {
    handleAdClick({ url }) {
      if (url) {
        window.open(url);
      }
    },
  },
};
</script>

<style scoped>
.list {
  margin: 10px 0;
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
}

.item {
  max-height: 150px;
  max-width: 690px;
}

.saperator {
  height: 2px;
  width: 100%;
  background-color: #f1f1f1;
  margin: 5px 0;
}
</style>
