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
          url: "https://i.sw13.icu/E6wn",
          img: "https://i.loli.net/2021/03/24/G15Fj3dLTcqDM74.jpg",
        },
        {
          url: "https://fastlink.so/auth/register?code=clashw",
          img: "https://download.fastlink.digital/fastlink_banner.jpg",
        },
        {
          url: "https://tly.llc",
          img: "https://tly.llc/asset/clash.gif",
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
