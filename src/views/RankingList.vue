<template>
  <div class="ranking-list">
    <!-- 这里放“排行榜的标题” -->
    <slot name="ranking-header"> 暂无数据 </slot>
    <div v-for="(itemData, index) in dataList" :key="`ranking-item-${index}`">
      <!-- 这里放“排行榜的每一项内容” -->
      <slot name="ranking-item" :data="itemData" :index="index">
        <span>
          {{ itemData.name }}: {{ itemData.value }} / {{ itemData.ratio }}
        </span>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ranking-list',
  props: {
    dataList: {
      type: Array,
    },
  },
};
</script>

<style scoped>
.ranking-list{
  width: 400px;
  margin: 0 auto;
}
</style>
