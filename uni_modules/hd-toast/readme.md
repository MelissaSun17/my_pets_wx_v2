# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-toast.html)
组件库提供更多vue3组件，比单独引入更加强大


# Toast 轻提示
在页面中间弹出提示，用于消息通知、加载提示、操作结果提示等场景。

## 代码演示

### 基础用法

```html
<!-- 在页面内添加对应的节点 -->
<hd-toast></hd-toast>

<button type="primary" @click="open">开启toast</button>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()

function open() {
  toast.showToast({
    title: '打开了'
  })
}
</script>

```


### 底色类型

通过`type`设置底色类型；`white`底色为白色，图标为多色；`black`底色为黑色，图标为白色；默认为`black`。

```html
<button type="primary" @click="open">开启toast</button>
<hd-toast></hd-toast>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()


function open() {
  toast.showToast({
    title: '打开了',
    type: 'white'
  })
}
</script>

```


### 提示内容

通过`title`设置提示内容。

```html
<button type="primary" @click="open">开启toast</button>
<hd-toast ></hd-toast>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()

function open() {
  toast.showToast({
    title: '这里是提示内容' 
  })
}
</script>

```

### 提示图标

通过`icon`设置提示图标；`success`: 显示成功图标；`warning`: 显示警告图标；`error`: 显示错误图标；`none`: 不显示图标。

```html
<button type="primary" @click="open">开启toast</button>
<hd-toast ></hd-toast>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()

function open() {
  toast.showToast({
    title: '这里是提示内容',
    icon: 'error' 
  })
}
</script>

```


### 自定义图标

通过`image`设置自定义图标，优先级大于`icon`。

```html
<button type="primary" @click="open">开启toast</button>
<hd-toast ></hd-toast>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()

function open() {
  toast.showToast({
    title: '这里是提示内容', icon: 'error', image: '' 
  })
}
</script>

```

### 提示持续时间

通过`duration`设置调整显示`toast`时间，单位毫秒，默认 1500 毫秒。

```html
<button type="primary" @click="open">开启toast</button>
<hd-toast ></hd-toast>
```

``` ts
<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from '@/uni_modules/hd-toast/components/hd-toast';

const toast = useToast()

function open() {
  toast.showToast({
    title: '这里是提示内容', icon: 'error', duration: 2000 
  })
}
</script>

```


## 方法

### `fant-mini` 中导出了以下 `Toast` 相关的辅助函数：

| 方法名    | 说明     | 参数           | 返回值      |
| --------- | -------- | -------------- | ----------- |
| showToast | 展示提示 | `ToastOptions` | `Toast`实例 |
| hideToast | 关闭提示 | `-`            | `-`         |

## `ToastOptions` 数据结构

### 调用 `showToast` 方法时，支持传入以下选项：

| 参数     | 说明                                                | 类型            | 是否必填 | 默认值  |
| -------- | --------------------------------------------------- | --------------- | -------- | ------- |
| type     | 底色类型，可选值:`white` `black`                    | `ToastType`     | `false`  | `black` |
| title    | 提示的内容。                                        | `String`        | `false`  | `-`     |
| icon     | 图标类型，可选值:`none` `success` `warning` `error` | `ToastIconType` | `false`  | `none`  |
| image    | 自定义图标的本地路径                                | `String`        | `false`  | `-`  |
| duration | 提示的持续时间                                      | `Number`        | `false`  | `1500`  |




## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|value|toast是否展示|`Boolean`|`false`|false|
|duration|toast展示时长(ms)，值为 0 时，notify 不会消失，默认值1500|`Number`|`false`|1500|
|title|toast提示的内容|`String`|`false`|-|
|type|toast底色类型|`'white'` / `'black'`|`false`|默认值是：`black`|
|icon|toast图标 - success: 显示成功图标 - warning: 显示警告图标 - error: 显示错误图标 - none: 不显示图标|`'success'` / `'none'`/ `'warning'`/ `'error'`|`false`|默认值是：`none`|
|image|toast自定义图片|`String`|`false`|-|
|zIndex|自定义层级，默认值 1000|`Number`|`false`|1000|
|id|组件唯一标识|`String`|`false`|-|




## Events

|Event Name|Description|Parameters|
|---|---|---|
|update:visible|消息展示状态变更时触发|value:Boolean 消息展示状态，建议通过v-model双向绑定输入值，而不是监听此事件的形式|
|被点击|被点击时触发|-|



## 联系我

有不明白或者建议可以扫码交流
#### QQ群
<img  src="https://fant-mini-plus.top/img/qq.jpg" width="220" height="auto">

#### 微信群
<img src="https://fant-mini-plus.top/img/weixin.png" width="220" height="auto">
