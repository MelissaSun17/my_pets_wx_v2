<template>
	<view class="box">
		<view class="content">
			<view class="content-search">
				<u-search @input="handleInput" placeholder="搜索地址" @focus='focus' height="72" :showAction="false"
					v-model="value"></u-search>
			</view>
			<!-- <view class="kongtai">
				<view class="kongtai_img">
					<image src="../../../static/空态图-什么都没有@3x.png" mode=""></image>
				</view>
				<view class="kongtai-text">
					找不到地址，请重新输入
				</view>
			</view> -->
			<view class="" v-show="!value">
				<view class="content-nearby">
					附近地址
				</view>
				<view class="content-nearby-list">
					<view class="content-nearby-list-text">
						徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
					</view>
					<view class="content-nearby-list-text">
						徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
					</view>
					<view class="content-nearby-list-text">
						徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
					</view>
				</view>
			</view>
			<view class="main-dizhi" v-show="value">
				<view class="main-dizhi-list">
					<view class="dizhi_list">
						<view class="main-dizhi-list-text2">
							徐汇区田林星巴克东南50米徐汇区田林星巴克东南50徐汇区田林星巴克东南50米
						</view>
						<view class="main-dizhi-list-text3">
							上海市徐汇区钦州路580号
						</view>
					</view>
					<view class="main-dizhi-list-mi">
						100m
					</view>
				</view>
				<view class="main-dizhi-list">
					<view class="dizhi_list">
						<view class="main-dizhi-list-text2">
							徐汇区田林星巴克东南50米徐汇区田林星巴克东南50徐汇区田林星巴克东南50米
						</view>
						<view class="main-dizhi-list-text3">
							上海市徐汇区钦州路580号
						</view>
					</view>
					<view class="main-dizhi-list-mi">
						100m
					</view>
				</view>
				<view class="main-dizhi-list">
					<view class="dizhi_list">
						<view class="main-dizhi-list-text2">
							徐汇区田林星巴克东南50米徐汇区田林星巴克东南50徐汇区田林星巴克东南50米
						</view>
						<view class="main-dizhi-list-text3">
							上海市徐汇区钦州路580号
						</view>
					</view>
					<view class="main-dizhi-list-mi">
						100m
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: '',
				// isComponent1Visible: true,
				// isComponent2Visible: false // 控制第二个组件的显示状态
			}
		},
		methods: {
			focus() {
				console.log(111);
			},
			handleInput() {
				if (this.value === '') {
					// 没有值时显示的组件
					this.showComponent = true;
				} else {
					// 有值时隐藏的组件
					this.showComponent = false;
				}
			}
		}
	}
</script>

<style lang="less" scoped>
	.content{
		background-color: #F6F6F6 ;
		height: 100vh;
	}
	.content-search {
		background-color: #FFFFFF;
		width: 670rpx;
		height: 72rpx;
		padding-left: 40rpx;
		margin-top: 24rpx;
		padding-right: 40rpx;
		padding-bottom: 48rpx;
		
	}

	.kongtai {
		width: 308rpx;
		margin: 156rpx auto;
		.kongtai_img{
			width: 280rpx;
			height: 280rpx;
			image{
				width: 280rpx;
				height: 280rpx;
			}
		}
		.kongtai-text{
			width: 308rpx;
			height: 40rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 28rpx;
			color: rgba(51,51,51,0.6);
			line-height: 40rpx;
			text-align: left;
			font-style: normal;
		}
	}

	/deep/.u-icon__icon.data-v-172979f2 {
		font-size: 50rpx !important;
	}

	.content-nearby {
		width: 750rpx;
		height: 40rpx;
		font-family: PingFangSC, PingFang SC;
		font-weight: 400;
		font-size: 28rpx;
		color: #999999;
		line-height: 40rpx;
		text-align: left;
		font-style: normal;
		text-transform: none;
		// padding-top: 48rpx;
		padding-left: 40rpx;
		background-color: #FFFFFF;
	}

	.content-nearby-list {
		width: 750rpx;
		background-color: #FFFFFF;
		.content-nearby-list-text {
			line-height: 128rpx;
			margin-left: 40rpx;
			margin-right: 40rpx;
			color: #000000;
			border-bottom: 2rpx solid #EBE9E9;
			white-space: nowrap;
			/* 不换行 */
			overflow: hidden;
			/* 隐藏溢出部分 */
			text-overflow: ellipsis;
			/* 显示省略号 */
		}
	}

	.main-dizhi {
		background-color: #FFFFFF;
		margin-top: 16rpx;

		.main-dizhi-top {
			width: 112rpx;
			height: 40rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 400;
			font-size: 28rpx;
			color: #999999;
			line-height: 33rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			margin-left: 40rpx;
			padding-top: 32rpx;
		}

		.main-dizhi-list {
			display: flex;
			justify-content: space-between;
			padding-bottom: 48rpx;
			border-bottom: 1rpx solid #EBE9E9;

			.dizhi_list {
				padding-left: 40rpx;

				.main-dizhi-list-text2 {
					width: 600rpx;
					height: 32rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 500;
					font-size: 28rpx;
					color: #000000;
					line-height: 32rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 40rpx;
					white-space: nowrap;
					/* 不换行 */
					overflow: hidden;
					/* 隐藏溢出部分 */
					text-overflow: ellipsis;
					/* 显示省略号 */
				}

				.main-dizhi-list-text3 {
					width: 600rpx;
					height: 34rpx;
					font-family: PingFang HK, PingFang HK;
					font-weight: 400;
					font-size: 24rpx;
					color: #999999;
					line-height: 28rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 16rpx;
					white-space: nowrap;
					/* 不换行 */
					overflow: hidden;
					/* 隐藏溢出部分 */
					text-overflow: ellipsis;
					/* 显示省略号 */
				}
			}

			.main-dizhi-list-mi {
				width: 100rpx;
				height: 32rpx;
				font-family: PingFang SC, PingFang SC;
				font-weight: 400;
				font-size: 28rpx;
				color: #666666;
				line-height: 32rpx;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-top: 64rpx;
			}
		}
	}
</style>