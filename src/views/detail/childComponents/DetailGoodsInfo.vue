<template>
  <div class="goods-info" v-if="Object.keys(goodsInfo).length !== 0">
    <div class="info-desc">
      <div class="desc">{{goodsInfo.desc}}</div>
    </div>
    <div class="info-key">{{goodsInfo.detailImage[0].key}}</div>
    <div class="info-list">
      <img v-for="(item, index) in goodsInfo.detailImage[0].list" :key="index" :src="item" alt="goods-img" @load="goodsInfoImgLoad">
    </div>
    <div></div>
  </div>
</template>

<script>
export default {
  name: 'DetailGoodsInfo',
  data() {
    return {
      imgCounter: 0,
      imgsLength: 0,
    }
  },
  props: {
    goodsInfo: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    goodsInfoImgLoad() {
      this.imgCounter++
      if (this.imgCounter === this.imgsLength) {
        // 所有图片都加载完，进行一次回调就行了
        this.$emit('goodsInfoImgLoad')
      }
    },
  },
  watch: {
    //   监听detailgoodsInfo里面值的变化， 只要发生改变就获取新的图片数量值
    goodsInfo: {
      handler() {
        this.imgsLength = this.goodsInfo.detailImage[0].list.length
      },
      deep: true,
    },
  },
}
</script>
<style scoped>
.goods-info {
  padding: 30px 8px 0;
  border-bottom: solid 4px rgba(100, 100, 100, 0.1);
}
.info-desc {
  padding: 0 8px 0;
  font-size: 14px;
}
.info-desc .desc {
  text-indent: 2em;
}
.info-key {
  padding: 8px;
}
.info-list img {
  width: 100%;
}
</style>
