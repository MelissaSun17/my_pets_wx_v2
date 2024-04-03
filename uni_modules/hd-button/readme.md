
# [组件库官方文档：fant-mini-plus](https://fant-mini-plus.top/fant-mini-plus/components/hd-button.html)
组件库提供更多vue3组件，比单独引入更加强大

# Button 按钮

按钮用于触发一个操作，如提交表单。  

## 代码演示

### 按钮类型

按钮支持 `default`、`primary`、`error`、`warning`、`success` 五种类型，默认为 `default`。

```html
<hd-button type="default">默认按钮</hd-button>
<hd-button type="primary">主要按钮</hd-button>
<hd-button type="error">危险按钮</hd-button>
<hd-button type="warning">警告按钮</hd-button>
<hd-button type="success">成功按钮</hd-button>
```

### 按钮尺寸

按钮支持 `normal`、`large`、`small`、`mini` 五种尺寸，默认为 `normal`。

```html
<hd-button type="default" size="normal">默认按钮（中等）</hd-button>
<hd-button type="primary" size="large">大号按钮</hd-button>
<hd-button type="default" size="small">小号按钮</hd-button>
<hd-button type="default" size="mini">迷你按钮</hd-button>
```

### 按钮形状

按钮支持 `square`直角、`roundsquare`小圆角、`round`全圆角 三种形状，默认为 `square`。

```html
<hd-button type="default" shape="square">直角</hd-button>
<hd-button type="default" shape="roundsquare">小圆角</hd-button>
<hd-button type="default" shape="round">全圆角</hd-button>
```

### 朴素按钮
通过`plain`属性将按钮设置为朴素按钮，朴素按钮的文字为按钮颜色，背景为白色。

```html
<hd-button plain type="primary">朴素按钮</hd-button>
<hd-button plain type="warning">朴素按钮</hd-button>
```

### 细边框

设置 `hairline` 属性可以展示 0.5px 的细边框。

```html
<hd-button plain type="primary">默认按钮</hd-button>
<hd-button plain hairline type="primary">细边框按钮</hd-button>
```

### 禁用状态

通过 `disabled` 属性来禁用按钮，禁用状态下按钮不可点击。

```html
<hd-button disabled type="primary">禁用状态</hd-button>
<hd-button disabled type="error">禁用状态</hd-button>
```

### 加载状态

通过 `loading` 属性设置按钮为加载状态。通过`loading-type`指定加载动画。

```html
<hd-button loading type="primary" />
<hd-button loading type="primary" loading-type="flower" loading-text="加载中..." />
```


### 自定义颜色
通过`color`属性可以自定义按钮的颜色。

```html
<hd-button color="#7232dd">单色按钮</hd-button>
<hd-button color="#7232dd" plain>单色按钮</hd-button>
<hd-button color="linear-gradient(to right, #4bb0ff, #6149f6)">
  渐变色按钮
</hd-button>
```


### 小程序能力

提供小程序按钮获取开放能力，详细见 [Props](#props) 和 [Events](#events);

开放能力，具体请看 uniapp 稳定关于 button 组件部分说明: [https://uniapp.dcloud.io/component/button](https://uniapp.dcloud.io/component/button);




## Props

|Name|Description|Type|Required|Default|
|---|---|---|---|---|
|type|按钮类型|`'default'` / `'primary'` / `'error'` / `'warning'` / `'success'`|`false`|默认值是：`default`|
|size|按钮尺寸|`'normal'` / `'large'` / `'small'` / `'mini'`|`false`|默认值是：`normal`|
|icon|左侧图标名称或图片链接，可选值见 Icon 组件|`String`|`false`|-|
|classPrefix|图标类名前缀，同 Icon 组件的 class-prefix 属性|`String`|`false`|fant-icon|
|plain|是否为朴素按钮|`Boolean`|`false`|false|
|block|是否为块级元素|`Boolean`|`false`|false|
|shape|按钮形状|`'square（直角）'` / `'roundsquare（小圆角）'` / `'round（大圆角）'`|`false`|默认值是：`roundsquare`|
|loading|是否显示为加载状态|`Boolean`|`false`|false|
|hairLine|是否细边框|`Boolean`|`false`|false|
|disabled|是否禁用按钮|`Boolean`|`false`|false|
|loadingText|加载状态提示文字|`String`|`false`|-|
|loadingSize|加载图标大小|`String`|`false`|40rpx|
|loadingType|加载状态图标类型|`'flower'` / `'circular'`|`false`|默认值:`circular`|
|color|按钮颜色，支持传入linear-gradient渐变色|`String`|`false`|-|
|customStyle|自定义样式|`String`|`false`|-|
|openType|开放能力，具体请看uniapp稳定关于button组件部分说明 https://uniapp.dcloud.io/component/button|`String`|`false`|-|
|formType|用于 `<form>` 组件，点击分别会触发 `<form>` 组件的 submit/reset 事件  取值为submit（提交表单），reset（重置表单）|`String`|`false`|-|
|appParameter|打开 APP 时，向 APP 传递的参数，open-type=launchApp时有效 只微信小程序、QQ小程序有效|`String`|`false`|-|
|hoverStopPropagation|指定是否阻止本节点的祖先节点出现点击态，微信小程序有效|`Boolean`|`false`|默认值是：`false`|
|lang|指定返回用户信息的语言，zh_CN 简体中文，zh_TW 繁体中文，en 英文。只微信小程序有效|`String`|`false`|默认值是：`en`|
|sessionFrom|会话来源，open-type="contact"时有效。只微信小程序有效|`String`|`false`|-|
|sendMessageTitle|会话内消息卡片标题，open-type="contact"时有效 默认当前标题，只微信小程序有效|`String`|`false`|-|
|sendMessagePath|会话内消息卡片点击跳转小程序路径，open-type="contact"时有效 默认当前分享路径，只微信小程序有效|`String`|`false`|-|
|sendMessageImg|会话内消息卡片图片，open-type="contact"时有效 默认当前页面截图，只微信小程序有效|`String`|`false`|-|
|showMessageCard|是否显示会话内消息卡片，设置此参数为 true，用户进入客服会话会在右下角显示"可能要发送的小程序"提示， 用户点击后可以快速发送小程序消息，open-type="contact"时有效|`Boolean`|`false`|默认值是：`false`|


## Events

|Event Name|Description|Parameters|
|---|---|---|
|click|点击按钮，且按钮状态不为加载或禁用时触发|-|
|getphonenumber|获取用户手机号回调	 open-type="getPhoneNumber"时有效（微信、支付宝、百度、字节、快手、京东小程序）|-|
|getuserinfo|用户点击该按钮时，会返回获取到的用户信息，从返回参数的detail中获取到的值同uni.getUserInfo（微信、QQ、百度、快手、京东小程序）|-|
|error|当使用开放能力时，发生错误的回调（微信、QQ、快手、京东小程序）|-|
|opensetting|在打开授权设置页并关闭后回调（微信、QQ、百度、快手、京东小程序）|-|
|launchapp|打开 APP 成功的回调（微信、QQ、快手、京东小程序）|-|
|chooseAvatar|获取用户头像回调（仅微信小程序支持）|-|


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


