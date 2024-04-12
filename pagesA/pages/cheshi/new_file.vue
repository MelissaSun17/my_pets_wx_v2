<template>
  <view class="container">
    <view v-for="(item, index) in items" :key="index">
      <view class="title" @click="toggleCollapse(index)">
        {{ item.title }}
        <text class="arrow">{{ item.collapsed ? '▼' : '▲' }}</text>
      </view>
      <view v-if="!item.collapsed" class="content">
        {{ item.content }}
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { title: '折叠面板1', content: '内容1', collapsed: true },
        { title: '折叠面板2', content: '内容2', collapsed: true },
        { title: '折叠面板3', content: '内容3', collapsed: true }
      ]
    };
  },
  methods: {
    toggleCollapse(index) {
      this.items[index].collapsed = !this.items[index].collapsed;
    }
  }
};
</script>

<style>
.container {
  margin-top: 20px;
}

.title {
  background-color: #f0f0f0;
  padding: 10px;
  border-bottom: 1px solid #ccc;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.arrow {
  font-size: 18px;
}

.content {
  padding: 10px;
}
</style>