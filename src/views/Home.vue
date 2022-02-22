<template>
  <div class="home">
    <h2>演示VUE作用域插槽</h2>
    <!-- 排名组件 -->
    <ranking-list :dataList="rankingList">
      <!-- 使用的是Home容器的数据 -->
      <template slot="ranking-header">
        <div style="margin-bottom: 20px; font-size: 22px">
          2022年冬奥会，共【{{ rankingList.length }}】个国家
        </div>
      </template>
      <!-- 使用的是ranking-list子容器的数据，slot只是提供样式 -->
      <template slot="ranking-item" slot-scope="slotProps">
        <div class="progress">
          <div class="progress-text">
            <span class="label"
              >{{ slotProps.index + 1 }} {{ slotProps.data.name }}</span
            >
            <span class="desc">{{ slotProps.data.value }}个</span>
          </div>
          <div
            class="progress-bar"
            :style="{ width: `${slotProps.data.ratio}%` }"
          ></div>
        </div>
      </template>
    </ranking-list>
  </div>
</template>

<script>
import RankingList from './RankingList.vue';

export default {
  name: 'Home',
  components: {
    RankingList,
  },
  data() {
    return {
      rankingList: [
        {
          name: '美国（USA）',
          value: 39,
          ratio: 100,
        },
        {
          name: '中国（CHN）',
          value: 38,
          ratio: 99,
        },
        {
          name: '日本（JPN）',
          value: 27,
          ratio: 39 / 27,
        },
        {
          name: '英国（GBR）',
          value: 22,
          ratio: 39 / 22,
        },
      ],
    };
  },
};
</script>

<style scoped>
.progress {
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
}

.progress-text {
  display: flex;
  justify-content: space-between;
}

.progress-bar {
  display: inline-block;
  height: 6px;
  background: rgba(254, 182, 57, 0.75);
  border-radius: 4px;
}
</style>
