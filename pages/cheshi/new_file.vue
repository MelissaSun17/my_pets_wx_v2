<template>
  <view class="baby-content">
    <view class="baby-content-neirong">
      <!-- 文本域 -->
      <textarea class="wenbenyu" v-model="textareaContent" rows="5"></textarea>
    </view>
    <view class="kuaijiejian">
      <!-- 标签 -->
      <view class="biaoqian" v-for="(tag, index) in tags" :key="index" @click="toggleContent(tag)">{{ tag }},</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      tags: ['害怕陌生人', '胆子很小', '喜欢所有人', '对猫很友好', '对狗很友好', '社牛', '爱玩玩具', '爱叫的话唠'],
      textareaContent: '' // 存储文本域中的内容
    };
  },
  methods: {
    toggleContent(tag) {
      // 检查文本域中是否已经包含了该标签内容
      if (this.textareaContent.includes(tag)) {
        // 如果包含，则移除该标签内容
        this.textareaContent = this.textareaContent.replace(tag + ', ', '').replace(tag, '').trim();
      } else {
        // 如果不包含，则添加该标签内容
        this.textareaContent += tag + ', ';
      }
    }
  }
}
</script>