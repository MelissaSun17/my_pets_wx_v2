<template>
  <view class="container_btn3">
    <view class="btn" :class="{ 'selected': isSelected(0, 3) }" @click="changeRange(0, 3)">1-3年</view>
    <view class="btn" :class="{ 'selected': isSelected(3, 5) }" @click="changeRange(3, 5)">3-5年</view>
    <view class="btn" :class="{ 'selected': isSelected(5, 7) }" @click="changeRange(5, 7)">5-7年</view>
    <view class="btn" :class="{ 'selected': isSelected(7, 10) }" @click="changeRange(7, 10)">7-10年</view>
    <view class="btn" :class="{ 'selected': isSelected(10, 30) }" @click="changeRange(10, 30)">10年以上</view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      selectedDistance: [0, 0] // 初始状态为未选中
    };
  },
  methods: {
    changeRange(min, max) {
      if (this.selectedDistance[0] === min && this.selectedDistance[1] === max) {
        // 如果当前选中的年限范围等于点击的年限范围，取消选中
        this.selectedDistance = [0, 0];
      } else {
        // 否则，设置为点击的年限范围
        this.selectedDistance = [min, max];
      }
    },
    isSelected(min, max) {
      // 判断当前按钮是否被选中
      return this.selectedDistance[0] === min && this.selectedDistance[1] === max;
    }
  }
};
</script>

<style>
.container_btn3 {
  display: flex;
}

.btn {
  margin-right: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  cursor: pointer;
}

.selected {
  background-color: #e0e0e0; /* 选中状态的背景颜色 */
}
</style>