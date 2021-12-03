<template>
  <div @click="show = !show" class="outdate-content">
    <div class="hint">部分内容已于 v{{ since }} 后过期，点击查看</div>
    <slot v-if="show" />
  </div>
</template>

<script>
export default {
  name: "Outdated",
  props: {
    since: String,
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style scoped>
.outdate-content {
  border: 1px solid #e6e6e6;
  padding: 10px;
  border-radius: 5px;
}

.hint {
  text-align: center;
  color: rgb(102, 102, 102);
  font-size: 14px;
  cursor: pointer;
}
</style>
