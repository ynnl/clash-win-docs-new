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
          url: "https://faster.goodfrog.net/wlS",
          img: "https://i.loli.net/2021/03/24/G15Fj3dLTcqDM74.jpg",
        },
        {
          url: "https://aaex.uk/cart.php?language=chinese",
          img: "https://api.crhnode.top/banner.png",
        },
        {
          url: "https://jike138.net/auth/register?code=LdON",
          img: "https://sy168.site/tupian/clash.jpg",
        },
        {
          url: "https://fastlink.ws/auth/register?code=clashw",
          img: "https://download.fastlink.digital/fastlink_banner.jpg",
        },
        {
          url: "http://cylink.wtf",
          img: "http://to.kache.moe/ad/clash_690_150.jpeg",
        },
        {
          url: "http://china-cdn-net.com/CFW",
          img: "https://ikuai349.obs.cn-south-1.myhuaweicloud.com/ChinaG.png",
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
