<template>
	<view class="">
		<view class="flex-box flex-wrap" v-if="type == '1'">
			<view class="check" v-for="(item,index) in list" :key="index"
				:style="[{'background':actives == index?activeBgColor:bgColor,'color':actives == index?activeTextColor:color},btnStyle]"
				@click="checkBtn(index,item)">
				<text class="texts" :style="{'fontSize':fontSize}">{{item[defaultProps.name]}}</text>
			</view>
		</view>
		<view class="flex-box flex-wrap" v-else>
			<view class="check" v-for="(item,index) in arr" :key="index"
				:style="[{'background':item.isCheck?activeBgColor:bgColor,'color':item.isCheck?activeTextColor:color},btnStyle]"
				@click="checkboxBtn(index,item)">

				<text class="texts" :style="{'fontSize':fontSize}">{{item[defaultProps.name]}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			/* 按钮列表 */
			list: {
				type: Array,
				default () {
					return []
				}
			},
			/* 默认字体颜色 */
			color: {
				type: String,
				default () {
					return "#666666"
				}
			},
			/* 选择字体颜色 */
			activeTextColor: {
				type: String,
				default () {
					return "#409dff"
				}
			},
			/* 默认背景色 */
			bgColor: {
				type: String,
				default () {
					return "#f6f6f6"
				}
			},
			/* 选择后的背景色 */
			activeBgColor: {
				type: String,
				default () {
					return "#cae4ff"
				}
			},
			/* 单选还是多选 */
			type: {
				type: String,
				default () {
					return "radio"
				}
			},
			/* 自定义按钮样式 */
			btnStyle: {
				type: Object,
				default () {
					return {}
				}
			},
			/* 自定义类名 */
			defaultProps: {
				type: Object,
				default: () => {
					return {
						name: 'name',
						id: 'id',
					}
				}
			},
			/* 单选选中 */
			active: {
				type: Number,
				default () {
					return 0
				}
			},
			/* 字体大小 */
			fontSize: {
				type: String,
				default () {
					return "24rpx"
				}
			},
		},
		data() {
			return {
				actives: this.active,
				arr: [],
				select: []
			}
		},
		watch: {
			active: {
				handler(nVal) {
					this.actives = nVal
				},
				immediate: true,
				deep: true
			}
		},
		mounted() {
			if (this.type == '2') {
				for (let i in this.list) {
					this.list[i].isCheck = false;
					this.arr.push(this.list[i])
				}
			}
		},
		methods: {
			/* 单选 */
			checkBtn(e, info) {
				// console.log(info)
				this.actives = e;
				info.idx = e;
				this.$emit("chooseItem", info)
			},
			/* 多选 */
			checkboxBtn(e, info) {
				// info.isCheck = true;
				let arr = [...this.arr];
				let selarr = [...this.select];
				if (arr[e].isCheck == false) {
					arr[e].isCheck = true;
					selarr.push(info)
				} else {
					arr[e].isCheck = false;
					var index11 = selarr.indexOf(e)
					selarr.splice(index11, 1)

				}
				this.arr = arr;
				this.select = selarr;
				this.$emit("chooseItem", this.select)
			}
		}
	}
</script>

<style scoped>
	.flex-wrap {
		flex-wrap: wrap;
	}

	/* flex横向左右两边布局*/

	.flex-space-between {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}


	/* flex垂直居中布局*/

	.flex-column {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}


	/* flex横向不居中布局 */

	.flex-box {
		display: flex;
		align-items: center;
	}


	/* flex横向居中布局 */

	.flex-center {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	/* flex横向平均布局 */

	.flex-space-around {
		display: flex;
		align-items: center;
		justify-content: space-around;
	}

	/* flex 布局 */
	.flex {
		display: flex;
		flex-direction: row;
	}

	/* flex1 */
	.flex1 {
		flex: 1;
	}

	.check {
		min-width: 100rpx;
		text-align: center;
		height: 50rpx;
		line-height: 50rpx;
		box-sizing: border-box;
		background-color: #f6f6f6;
		color: #666666;
		border-radius: 10rpx;
		margin: 10rpx 10rpx;
	}


	/* .check:nth-child(3n) {
		margin-right: 0;
	} */

	.check_y {
		background-color: #cae4ff;
		color: #409dff;
	}
</style>