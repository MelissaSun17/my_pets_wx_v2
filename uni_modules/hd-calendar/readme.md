# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-calendar.html)
组件库提供更多vue3组件，比单独引入更加强大

# Calendar 日历

日历组件用于选择日期或日期区间。

## 代码演示

### 选择单个日期

下面演示了结合单元格来使用日历组件的用法，日期选择完成后会触发 `confirm` 事件,返回的 date 为数组。

```html
<hd-cell title="选择单个日期" :value="date" @click="showCalendar" isLink />
<hd-calendar mode="single" @confirm="confirm" />
```

```ts
<script lang="ts" setup>
import { useCalendar } from '@/uni_modules/hd-calendar/components/hd-calendar';
const calendar = useCalendar()
const date = ref<number>(new Date().getTime())
function showCalendar(){
  calendar.showCalendar()
}
function confirm(e) {
  date.value =CommonUtil.deepClone(e)
}
</script>
```

### 选择多个日期

设置 `mode` 为 `multiple` 后可以选择多个日期，此时 `confirm` 事件返回的 date 为数组结构，数组包含若干个选中的日期。

```html
<hd-cell title="选择多个日期" :value="date" @click="showCalendar" isLink />
<hd-calendar mode="multiple" @confirm="confirm" />
```

```ts
<script lang="ts" setup>
import { useCalendar } from '@/uni_modules/hd-calendar/components/hd-calendar';

const calendar = useCalendar()
const date = ref<number>([])
function showCalendar(){
  calendar.showCalendar()
}
function confirm(e) {
  date.value =CommonUtil.deepClone(e)
}
</script>
```

### 选择日期区间

设置 `mode` 为 `range` 后可以选择日期区间，此时 `confirm` 事件返回的 date 为数组结构，数组为范围内的时间的集合。

```html
<hd-cell title="选择日期区间" :value="date" @click="showCalendar" isLink />
<hd-calendar mode="range" @confirm="confirm" />
```

```ts
<script lang="ts" setup>
import { useCalendar } from '@/uni_modules/hd-calendar/components/hd-calendar';

const calendar = useCalendar()
const date = ref<number>([])
function showCalendar(){
  calendar.showCalendar()
}
function confirm(e) {
  date.value =CommonUtil.deepClone(e)
}
</script>
```

> Tips: 默认情况下，日期区间的起止时间不能为同一天，可以通过设置 allow-same-day 属性来允许选择同一天。

### 快捷选择

将 `show-confirm` 设置为 `false` 可以隐藏确认按钮，这种情况下选择完成后会立即触发 `confirm` 事件。

```html
<hd-calendar :show-confirm="false" @confirm="confirm" />
```

```ts
<script lang="ts" setup>
import { useCalendar } from '@/uni_modules/hd-calendar/components/hd-calendar';

const calendar = useCalendar()
const date = ref<number>(new Date().getTime())
function showCalendar(){
  calendar.showCalendar()
}
function confirm(e) {
  date.value =CommonUtil.deepClone(e)
}
</script>
```

### 自定义颜色

通过 `color` 属性可以自定义日历的颜色，对选中日期和底部按钮生效。

```html
<hd-calendar color="#1989fa" />
```

### 自定义日期范围

通过 `min-date` 和 `max-date` 定义日历的范围。

```html
<hd-calendar :min-date="minDate" :max-date="maxDate" />
```

```ts
const minDate = Date.now()
const maxDate = new Date(new Date().getFullYear(), new Date().getMonth() + 6, new Date().getDate()).getTime()
```

### 自定义按钮文字

通过 `confirm-text` 设置按钮文字，通过 `confirm-disabled-text` 设置按钮禁用时的文字。

```html
<hd-calendar mode="range" confirm-text="完成" confirm-disabled-text="请选择结束时间" />
```

### 自定义日期文案

通过传入 `formatter` 函数来对日历上每一格的内容进行格式化。

```html
<hd-calendar mode="range" :formatter="formatter" />
```

```ts
function formatter(day) {
  const month = new Date(day.timestamp).getMonth() + 1
  const date = new Date(day.timestamp).getDate()
  if (month === 5) {
    if (date === 1) {
      day.topTip = '劳动节'
    } else if (date === 4) {
      day.topTip = '五四青年节'
    } else if (date === 11) {
      day.date = '今天'
    }
  }
  if (day.type === 'start') {
    day.bottomTip = '入店'
  } else if (day.type === 'end') {
    day.bottomTip = '离店'
  }
  return day
}
```

#### Day 数据结构

| 键名      | 说明                                                      | 类型                |
| --------- | --------------------------------------------------------- | ------------------- |
| date      | 当前日期的`天`的数值                                      | `number` / `string` |
| day       | 当前星期几                                                | `number` / `string` |
| timestamp | 当前日期时间戳                                            | `number`            |
| type      | 日期类型，可选值为 selected、start、middle、end、disabled | `string`            |
| style     | 当前日期样式                                              | `string`            |
| topTip    | 上方的提示信息                                            | `string`            |
| bottomTip | 下方的提示信息                                            | `string`            |
| className | 自定义 className                                          | `string`            |

### 日期区间最大范围

选择日期区间时，可以通过 `max-range` 属性来指定最多可选天数，选择的范围超过最多可选天数时，会弹出相应的提示文案。

```html
<hd-calendar mode="range" :max-range="3" :style="{ height: '500px' }" />
```

### 其余属性

其余属性请在下方 [Props](#props) 自行探索




## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|title|日历标题|`String`|`false`|日期选择|
|showTitle|是否显示标题|`Boolean`|`false`|true|
|showSubtitle|是否展示日历副标题（年月）|`Boolean`|`false`|true|
|mode|日期选择类型|`'single（选择单个日期）'` / `'multiple（选择多个日期）'` / `'range（选择日期范围）'`|`false`|single|
|color|主题色，对底部按钮和选中日期有效|`String`|`false`|#1C64FD|
|minDate|可选择的最小日期|`Number`|`false`|initialMinDate|
|maxDate|可选择的最大日期|`Number`|`false`|initialMaxDate|
|defaultDate|默认选中的日期，mode 为 multiple 或 range 时为数组，传入 null/[] 表示默认不选择|`Number` /  `Array`|`false`|null|
|rowHeight|日期行高|`String` /  `Number`|`false`|128|
|formatter|日期格式化函数|`Function`|`false`|-|
|showMark|是否显示月份背景色|`Boolean`|`false`|true|
|confirmText|确定按钮的文字|`String`|`false`|确定|
|confirmDisabledText|确认按钮处于禁用状态时的文字|`String`|`false`|确定|
|maskClick|是否允许点击遮罩关闭日历|`Boolean`|`false`|true|
|readonly|是否为只读状态，只读状态下禁止选择日期|`Boolean`|`false`|false|
|showConfirm|是否展示确认按钮|`Boolean`|`false`|true|
|maxRange|日期区间最多可选天数，默认无限制，mode = range时有效|`Number`|`false`|Number.MAX_SAFE_INTEGER|
|rangePrompt|范围选择超过最多可选天数时的提示文案，mode = range时有效|`String`|`false`|-|
|showRangePrompt|范围选择超过最多可选天数时，是否展示提示文案，mode = range时有效|`Boolean`|`false`|true|
|allowSameDay|是否允许日期范围的起止时间为同一天，mode = range时有效|`Boolean`|`false`|false|
|round|圆角值|`Boolean` /  `String` /  `Number`|`false`|0|
|id|组件唯一标识|`String`|`false`|-|




## Events

|Event Name|Description|Parameters|
|---|---|---|
|unselect|当 Calendar 的 type 为 multiple 时,点击已选中的日期时触发|value: Number|
|select|点击任意日期时触发|value: Number | Number[]|
|confirm|日期选择完成后触发，若show-confirm为true，则点击确认按钮后触发|value: Number | Number[]|
|close|关闭弹出层时触发|-|



## Methods

|Method|Description|Parameters|
|---|---|---|
|close|主动关闭|-|
|open|主动打开|-|



## 联系我

有不明白或者建议可以扫码交流
#### QQ群
<img  src="https://fant-mini-plus.top/img/qq.jpg" width="220" height="auto">

#### 微信群
<img src="https://fant-mini-plus.top/img/weixin.png" width="220" height="auto">