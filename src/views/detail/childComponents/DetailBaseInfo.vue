<template>
  <div v-if="Object.keys(goods).length!==0" class="base-info">
    <div class="info-title">{{goods.title}}</div>
    <div class="info-price">
      <span class="n-price">{{goods.newPrice}}</span>
      <span class="o-price">{{goods.oldPrice}}</span>
      <span class="discount" v-if="goods.discount">{{goods.discount}}</span>
    </div>
    <div class="info-other">
      <span>{{goods.columns && goods.columns[0]}}</span>
      <span>{{goods.columns && goods.columns[1]}}</span>
      <span>{{goods.services && goods.services[ goods.services.length-1].name}}</span>
    </div>
    <div class="info-service" v-if="goods.services">
      <span class="info-service-item" v-for="index in goods.services.length-1" :key="index">
        <img :src="goods.services[index-1].icon" alt="icon">
        <span>{{goods.services[index-1].name}}</span>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailBaseInfo',
  props: {
    goods: {
      type: Object,
      default() {
        return {}
      },
    },
  },
}
</script>

<style scoped>
.base-info {
  width: 100%;
  padding: 10px 10px 20px;
  border-bottom: solid 4px rgba(100, 100, 100, 0.1);
}
.info-title {
  font-size: 16px;
  font-weight: bold;
}
.info-price {
  margin-top: 8px;
}
.info-price .n-price {
  color: var(--color-high-text);
  font-size: 20px;
  margin-right: 8px;
}
.info-price .o-price {
  color: var(--color-text);
  text-decoration: line-through;
  font-size: 12px;
  margin-right: 4px;
}
.info-price .discount {
  background: var(--color-tint);
  color: #fff;
  font-weight: bold;
  border-radius: 8px;
  position: relative;
  top: -8px;
}
.info-other {
  margin-top: 12px;
  font-size: 14px;
  display: flex;
  color: var(--color-text);
  padding-bottom: 4px;
  justify-content: space-between;
  border-bottom: solid 2px rgba(100, 100, 100, 0.3);
}
.info-service {
  margin-top: 18px;
  display: flex;
  justify-content: space-between;
  font-size: 14px;
}
.info-service img {
  width: 12px;
  height: 12px;
}
</style>

