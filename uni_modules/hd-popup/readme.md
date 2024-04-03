
# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-popup.html)
组件库提供更多vue3组件，比单独引入更加强大


# Popup 弹出层
弹出层容器，用于展示弹窗、信息提示等内容。

## 代码演示

### 基础用法

``` html
<button type="primary" @click="openPop">开启弹出框</button>
<hd-popup>
  <view>
    这是一个简单的弹出框
  </view>
</hd-popup>
```
```ts
<script lang="ts" setup>
import { ref } from 'vue'
import { usePopup } from '../../uni_modules/hd-popup/components/hd-popup';

const popup = usePopup()

function openPop() {
  popup.showPopup()
}

function closePop() {
  popup.closePopup()
}
</script>

```

### 弹出框位置

通过`type`属性设置弹出位置，默认全屏弹出层(`center`)，可以设置`top（ 顶部弹出层）` 、`bottom（底部弹出层）` 、`left（左侧弹出层）`、`bottom（右侧弹出层）`或 `center（全屏弹出层）`。

``` html
<button type="primary" @click="openPop" :type="type">开启弹出框</button>
<hd-popup>
  <view>
    这是一个简单的弹出框
  </view>
</hd-popup>
```
```ts
<script lang="ts" setup>
import { ref } from 'vue'
import { usePopup } from '../../uni_modules/hd-popup/components/hd-popup';

const popup = usePopup()

function openPop() {
  popup.showPopup()
}

function closePop() {
  popup.closePopup()
}
</script>

```

### 关闭弹出框

通过`maskClick`属性控制点击蒙层是否关闭弹出框，默认允许点击蒙层关闭(`maskClick`为`true`)，当不允许点击蒙层关闭时，可以手动关闭弹出框。

``` html
<hd-popup :maskClick="maskClick">
  <view>
    这是一个简单的弹出框
    <view v-if="!maskClick" @click="closePop">
      <!-- 关闭按钮 -->
      <hd-icon name="ic_circleclose_line" size="48rpx"></hd-icon>
    </view>
  </view>
</hd-popup>
```

```ts
<script lang="ts" setup>

import { ref } from 'vue'
import { usePopup } from '../../uni_modules/hd-popup/components/hd-popup';

const popup = usePopup() 

const maskClick = ref<boolean>(false)

function openPop() {
  popup.showPopup()
}

function closePop() {
  popup.closePopup()
}
</script>

```




## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|animation|开启动画|`Boolean`|`false`|true|
|type|弹出层类型|`'top（ 顶部弹出层）'` / `'bottom（底部弹出层）'` / `'left（左侧弹出层）'`/ `'right（右侧弹出层）'`/ `'center（全屏弹出层）'`|`false`|默认值：'center'|
|overlay|是否显示遮罩|`Boolean`|`false`|true|
|maskClick|是否允许点击蒙层关闭|`Boolean`|`false`|默认值：true|
|backgroundColor|背景颜色|`String`|`false`|none|
|duration|动画时长，单位ms|`Number`|`false`|300|
|overlayOpacity|遮罩的透明度，0-1之间|`Number`|`false`|0.4|
|zIndex|自定义层级|`Number`|`false`|999|
|id|组件唯一标识|`String`|`false`|-|


## Events

|Event Name|Description|Parameters|
|---|---|---|
|change|-|-|
|close|弹层关闭时触发|-|
|maskClick|遮罩被点击时触发|-|
|click|-|-|


## Slots

|Name|Description|Default Slot Content|
|---|---|---|
|default|-|-|

## 联系我

有不明白或者建议可以扫码交流
#### QQ群
<img  src="https://fant-mini-plus.top/img/qq.jpg" width="220" height="auto">

#### 微信群
<img src="https://fant-mini-plus.top/img/weixin.png" width="220" height="auto">
