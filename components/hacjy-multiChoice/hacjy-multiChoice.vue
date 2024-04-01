<template>
	<view class="multi-content" :class="{'multi-content-wrap':wrap,}"
		:style="{paddingLeft:offset+'px',paddingRight:offset+'px','--col':col,'--height':height,
	'--rowGap':rowGap,'--columnGap':columnGap,'--marginTop':marginTop,justifyContent:justifyContent,'--backgroundColor':backgroundColor,}">
		<view v-for="(item,index) in list" :key="index" class="normal"
			:class="{'selected':item.checked==true,'border-box':border}" :style="{minWidth:wrap?width:'auto',color:item.checked?selectedTextColor:normalTextColor,
			borderColor:item.checked?selectedBorderColor:normalBorderColor}" @click="clickGrid(index)">
			<text class="name-txt">{{item.name}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		name: "multiChoice",
		props: {
			//列表数据
			list: { //{name,id,checked}
				type: Array,
				default () {
					return []
				}
			},
			//是否单选
			radio: {
				type: Boolean | String,
				default: false
			},
			//是否是Wrap布局
			wrap: {
				type: Boolean,
				default: false
			},
			justifyContent: {
				type: String,
				default: 'flex-start'
			},

			//是否显示边框 默认显示
			border: {
				type: Boolean,
				default: true
			},
			//是否是只读
			onlyRead: {
				type: Boolean,
				default: false
			},
			//几列
			col: {
				type: Number,
				default: 3
			},
			//偏移量
			offset: {
				type: Number,
				default: 0
			},
			//最小宽度
			width: {
				type: String,
				default: '48px'
			},
			//高度
			height: {
				type: String,
				default: '40px'
			},
			//顶部距离
			marginTop: {
				type: String,
				default: '0px'
			},
			//行间距
			rowGap: {
				type: String,
				default: '9px'
			},
			//列间距
			columnGap: {
				type: String,
				default: '10px'
			},
			//选中的字体颜色
			selectedTextColor: {
				type: String,
				default: '#FF8730'
			},
			//选中的border颜色
			selectedBorderColor: {
				type: String,
				default: '#FF8730'
			},
			//正常的字体颜色
			normalTextColor: {
				type: String,
				default: '#404142'
			},
			//正常的border颜色
			normalBorderColor: {
				type: String,
				default: '#C5C5C5'
			},
			//背景颜色
			backgroundColor: {
				type: String,
				default: '#F6F6F6'
			},
		},
		watch: {
			//通过监听处理数据 避免在created时数据还在请求从而拿到默认数据
			list: {
				handler(newVal, oldVal) {
					//处理数据
				},
				immediate: true, // //immediate:true代表如果在 wacth 里声明了之后，就会立即先去执行里面的handler方法，如果为 false，不会在绑定的时候就执行。
				deep: true //默认值是 false，代表是否深度监听
			}
		},
		data() {
			return {
				lastIndex: -1
			}
		},
		created() {},
		methods: {

			clear() {
				console.log('clear')
				this.list = []
				this.lastIndex = -1
			},
			clickGrid(index) {
				if (this.onlyRead)
					return
				if (this.radio) {
					this.radioClick(index)
				} else {
					this.checkboxClick(index)
				}
			},
			checkboxClick(index) {
				console.log('checkboxClick', index)
				this.list[index].checked = !this.list[index].checked
				this.$set(this.list, index, this.list[index])
				this.$emit('refresh', this.list)
			},
			radioClick(index) {
				console.log('radioClick', index)
				if (this.lastIndex >= 0) {
					this.list[this.lastIndex].checked = !this.list[this.lastIndex].checked
					this.$set(this.list, this.lastIndex, this.list[this.lastIndex])
				}
				//如果上次选中的跟这次是同一个item，就不继续处理了
				if (this.lastIndex == index) {
					return
				}
				this.lastIndex = index
				this.list[index].checked = !this.list[index].checked
				this.$set(this.list, index, this.list[index])
				this.$emit('refresh', this.list)
			},
			getCheckedData() {
				var result = []
				for (var i = 0; i < this.list.length; i++) {
					if (this.list[i].checked) {
						result.push(this.list[i])
					}
				}
				return result
			}
		}
	}
</script>

<style scoped lang="scss">
	.multi-content {
		width: 100%;
		box-sizing: border-box;
		margin-top: var(--marginTop);

		//网格布局
		display: grid;
		justify-content: center;
		//var(col) 动态赋值
		//几列 每列等宽
		grid-template-columns: repeat(var(--col), 1fr);
		// grid-template-rows: repeat(var(--col), var(--height));
		//row-gap属性设置行与行的间隔（行间距）
		row-gap: var(--rowGap);
		//column-gap属性设置列与列的间隔（列间距）。
		column-gap: var(--columnGap);
	}

	.multi-content-wrap {
		width: 100%;
		box-sizing: border-box;
		margin-top: var(--marginTop);

		//Wrap布局
		display: flex;
		justify-content: flex-start;
		flex-wrap: wrap;
	}

	.normal {
		display: flex;
		justify-content: center;
		align-content: center;
		align-items: center;

		border-radius: 12rpx;
		color: #404142;
		text-align: center;
		background: var(--backgroundColor);
		height: var(--height);
	}

	.border-box {
		border: 1rpx solid #C5C5C5;
		;
	}

	.selected {
		background: rgba(255, 135, 48, 0.1);
		border-color: #FF8730;
		color: #FF8730;
	}

	.name-txt {
		width: 100%;
		font-size: 32rpx;
		text-align: center;
		padding: 16rpx;
		flex: 1;
	}
</style>