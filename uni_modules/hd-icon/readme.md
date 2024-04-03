# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-icon.html)
文档中点击对应图标即可复制，同时组件库提供更多vue3组件，比单独引入更加强大


# Icon 图标

基于字体的图标集，可以通过 Icon 组件使用，也可以在其他组件中通过 icon 属性引用。
## 代码演示

### 基础用法

`name` 图标名称或图片链接,`color` 图标颜色，`size` 图标大小，如 20px，2em，默认单位为px。
``` html
<hd-icon name="ic_scan_line" color="#333" size="20px"></hd-icon>
```

### 自定义样式

`customStyle` 自定义图标样式，style行内样式。
``` html
<hd-icon name="ic_scan_line" :color="#333" size="20px" customStyle="color: #999"></hd-icon>
```

### 自定义类名前缀

`classPrefix` 自定义类名前缀，默认值fant-icon。
``` html
<hd-icon name="ic_scan_line" color="#333" size="20px" classPrefix="f-ic"></hd-icon>
```

### 事件

`click`事件, 当icon组件被点击时触发。

``` html
<hd-icon name="ic_scan_line" color="#333" size="20px" @click="click"></hd-icon>

```



## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|name|图标名称或图片链接|`String`|`false`|-|
|color|图标颜色|`String`|`false`|默认值:#CFD3DB|
|size|图标大小|`String` /  `Number`|`false`|-|
|customStyle|自定义样式|`String`|`false`|-|
|classPrefix|自定义类名前缀|`String`|`false`|默认值：fant-icon|


## Events

|Event Name|Description|Parameters|
|---|---|---|
|click|图标被点击时触发|无|


## 联系我

有不明白或者建议可以扫码交流
#### QQ群
<img  src="https://fant-mini-plus.top/img/qq.jpg" width="220" height="auto">

#### 微信群
<img src="https://fant-mini-plus.top/img/weixin.png" width="220" height="auto">



