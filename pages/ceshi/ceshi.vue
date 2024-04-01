<template>
  <view class="container">
    <!-- 页面内容区域 -->
    <view class="content">
      <text>{{ message }}</text>
    </view>

    <!-- 自定义底部导航栏 -->
    <view class="custom-tab-bar">
      <view class="tab-item" :class="{ active: currentTab === 'home' }" @click="changeTab('home')">首页</view>
      <view class="tab-item" :class="{ active: currentTab === 'discover' }" @click="changeTab('discover')">发现</view>
      <view class="tab-item" :class="{ active: currentTab === 'profile' }" @click="changeTab('profile')">个人中心</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      currentTab: 'home', // 默认选中首页
      message: 'Welcome to Uni-App!'
    };
  },
  methods: {
    // 切换底部导航栏选项
    changeTab(tab) {
      this.currentTab = tab;
    }
  }
};
</script>

<style>
.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.custom-tab-bar {
  display: flex;
  justify-content: space-around;
  background-color: #f0f0f0;
  height: 50px;
}

.tab-item {
  flex: 1;
  text-align: center;
  line-height: 50px;
  font-size: 16px;
  color: #333;
  cursor: pointer;
}

.tab-item.active {
  color: #007bff;
}
</style>