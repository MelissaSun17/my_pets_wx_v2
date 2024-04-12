<template>
  <div>
    <!-- 步骤1 -->
    <div :class="{ 'step': true, 'active': currentStep === 1, 'completed': currentStep >= 1 }" @click="setCurrentStep(1)">
      <!-- 使用背景图片作为状态标识 -->
      Step 1
    </div>
    <div class="divider"></div> <!-- 中间虚线 -->
    <!-- 步骤2 -->
    <div class="step" :class="{ 'active': currentStep === 2, 'completed': currentStep >= 2 }" @click="setCurrentStep(2)">
      <!-- 使用背景图片作为状态标识 -->
      Step 2
    </div>
    <div class="divider"></div> <!-- 中间虚线 -->
    <!-- 步骤3 -->
    <div class="step" :class="{ active: currentStep === 3, 'completed': currentStep >= 3 }" @click="setCurrentStep(3)">
      <!-- 使用背景图片作为状态标识 -->
      Step 3
    </div>
    <!-- 下一步按钮 -->
    <button @click="nextStep">下一步</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentStep: 1 // 当前步骤
    };
  },
  methods: {
    setCurrentStep(step) {
      // 如果点击第一步，则直接跳到第二步
      if (step === 1) {
        this.currentStep = 2;
      } else {
        this.currentStep = step;
      }
    },
    nextStep() {
      // 切换到下一步
      if (this.currentStep < 3) {
        this.currentStep++;
        // 如果当前步骤是第二步，则将其状态设置为完成
        if (this.currentStep === 2) {
          setTimeout(() => {
            this.currentStep = 2;
          }, 500); // 延迟一段时间以便触发 CSS 动画效果
        }
      } else {
        this.currentStep = 1; // 重置到第一步
      }
    }
  }
};
</script>

<style>
/* 步骤样式 */
.step {
  display: inline-block;
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  border: 1px solid #ccc;
  cursor: pointer;
  margin-right: 10px;
  transition: background-color 0.3s ease;
}

/* 当前步骤的样式 */
.step.active {
  background-color: #007bff;
  color: #fff;
}

/* 完成步骤的样式 */
.step.completed {
  /* 使用背景图片表示完成状态 */
  background-image: url('../../../static/logo.png');
  background-size: cover;
}

/* 中间虚线样式 */
.divider {
  display: inline-block;
  height: 1px;
  width: 50px; /* 虚线宽度 */
  border-top: 1px dashed #ccc; /* 虚线样式 */
  margin-right: 10px;
  vertical-align: middle; /* 垂直居中 */
}
</style>