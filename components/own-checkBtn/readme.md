## 使用说明
|  参数				|  格式	|  说明							|
|  ----				| ----	|----							|
| list				| Array	| [{name:"按钮"}] 或者 ["按钮"]	|
| activeTextColor	| String|选中背景色 "#fff"				|
| bgColor			| String|选中字体色 "#fff"				|
| bgColor			| String|选中字体色 "#fff"				|
| color				| String|未选中字体色 "#fff"			|
| type				| String| 单选还是多选 1/2				|
| defaultProps		| Object| 自定义name和id				|
| btnStyle			| Object| 自定义按钮样式				|
| fontSize			| String| 文字大小						|

```javascript
<own-check :list="list" color="#fff"
   bgColor="#55aa00"
   activeTextColor="#fff"
   activeBgColor="#ff5500"
   type="1"
   :defaultProps="defaultProps"
   fontSize="22rpx"
   @chooseItem="chooseItems"
>
</own-check>


import ownCheck from '@/components/own-checkBtn/own-check.vue'; //多选单选自定义按钮

export default {
		components: {
			ownCheck
		},
		data() {
			return {
				defaultProps: {
					name: "label",
					id: "value"
				},
			}
		},
		methods:{
			chooseItems(e){
				
			}
		}
	}
```
