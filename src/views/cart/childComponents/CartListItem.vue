<template>
  <div class="cart-list-item">
    <div class="item-selector">
      <check-button :isChecked="goodsItem.checked" @click.native="btnClick"></check-button>
    </div>
    <!-- <check-goods-btn :isSelected="goodsItem.isSelected" @click.native="handleSelectGoods(goodsItem)" /> -->
    <div class="goods-img">
      <img :src="goodsItem.image" alt="goods_img">
    </div>
    <div class="goods-info">
      <div class="title">{{goodsItem.title}}</div>
      <div class="desc">{{goodsItem.desc}}</div>
      <div class="price_num">
        <div class="price">{{goodsItem.price}}</div>
        <div class="num">X{{goodsItem.count}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import CheckButton from '@/components/content/checkButton/CheckButton.vue'

export default {
  data() {
    return {}
  },
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  components: {
    CheckButton,
  },
  methods: {
    btnClick() {
      this.goodsItem.checked = !this.goodsItem.checked
    },
  },
}
</script>

<style scoped lang="less">
.cart-list-item {
  width: 100%;
  padding: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 2px solid rgba(100, 100, 100, 0.2);
}
.item-selector {
  width: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.goods-img {
  padding: 5px;
}
.goods-img img {
  width: 80px;
  height: 110px;
  border-radius: 5px;
}
.goods-info {
  width: 65%;
  padding: 5px 10px;
  overflow: hidden;
  font-size: 17px;
  color: #333;
}
.goods-info .title,
.goods-info .desc {
  width: 100%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.goods-info .desc {
  margin-top: 10px;
  font-size: 14px;
  color: #666;
}
.goods-info .price_num {
  padding: 8px 5px;
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
}
.goods-info .price_num .price {
  color: var(--color-high-text);
  /* font-size: 20px; */
  font-weight: bold;
}
</style>