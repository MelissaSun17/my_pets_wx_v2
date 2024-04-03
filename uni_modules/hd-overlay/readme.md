# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-overlay.html)
组件库提供更多vue3组件，比单独引入更加强大

# Overlay 遮罩层
创建一个遮罩层，用于强调特定的页面元素，并阻止用户进行其他操作。
## 代码演示

### 基础用法

```HTML
<hd-button type="primary" @click="Show">显示遮罩层</hd-button>
<hd-overlay :show="show" @click="Hide" />
```

```ts

const show = ref<boolean>(false)

function Show() {
  show.value = true
}
function Hide() {
  show.value = false
}
```

### 嵌入内容

通过默认插槽可以在遮罩层上嵌入任意内容。

```html
<hd-button type="primary" @click="Show">嵌入内容</hd-button>
<hd-overlay :show="show" @click="Hide">
  <view class="wrapper">
    <div class="block" />
  </view>
</hd-overlay>
```

```ts

const show = ref<boolean>(false)

function Show() {
  show.value = true
}
function Hide() {
  show.value = false
}
```

```css
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.block {
  width: 120px;
  height: 120px;
  background-color: #fff;
}
```




## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|show|是否显示遮罩|`Boolean`|`false`|默认 false|
|customStyle|自定义样式|`String`|`false`|-|
|duration|动画时长，单位毫秒|`Number`|`false`|默认 300|
|zIndex|自定义层级|`Number`|`false`|1|
|lockScroll|是否锁定背景滚动，锁定时蒙层里的内容也将无法滚动|`Boolean`|`false`|默认 false|
|opacity|不透明度值，当做rgba的第四个参数|`String` /  `Number`|`false`|0.5|


## Events

|Event Name|Description|Parameters|
|---|---|---|
|click|遮罩被点击时触发|-|



## Slots

|Name|Description|Default Slot Content|
|---|---|---|
|default|-|-|
|default|-|-|



## 联系我

有不明白或者建议可以扫码交流
#### QQ群
<img  src="https://fant-mini-plus.top/img/qq.jpg" width="220" height="auto">

#### 微信群
<img src="https://fant-mini-plus.top/img/weixin.png" width="220" height="auto">


