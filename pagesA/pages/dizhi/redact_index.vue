<template>
	<view class="box">
		<view class="content">
			<view class="content-dizhi" @click="selectAddress">
				<view class="content-dizhi-text">
					地址
				</view>
				<view class="content-dizhi-seek">
					<view class="dizhi-seek-text" :class="{ 'selecteddizhi': dizhiColor }">
						请选择服务地址
						请选择服务地址
						请选择服务地址
						请选择服务地址
						请选择服务地址
						请选择服务地址
					</view>
					<view class="dizhi-seek-icon-right">
						<image src="../../../static/icon_arrow@3x.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="content-number">
				<view class="content-number-text">
					门牌号
				</view>
				<view class="content-number-box">
					<view class="content-number-box-text">
						请填写详细地址，例1号楼101 请填写详细地址，例1号楼101 请填写详细地址，例1号楼101
					</view>
				</view>
			</view>
			<view class="new-button" @click="openRedact(item)" :titleStyle="{fontWeight: 500}"
				v-for="(item, index) in list"
				:key="index"
				isLink
				>
				确认编辑
			</view>
			<u-toast ref="uToast"></u-toast>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: false,
				list: [
					{
						type: 'success',
						message: "地址编辑成功～",
						iconUrl: 'https://cdn.uviewui.com/uview/demo/toast/success.png'
					}
				],
			}
		},
		computed: {
			getIcon() {
				return path => {
					return 'https://cdn.uviewui.com/uview/example/' + path + '.png';
				}
			},
		},
		methods: {
			selectAddress() {
				uni.navigateTo({
					url: ('/pagesA/pages/newDiZhi/new_dizhi')
				})
			},
	
			openRedact(params) {
				this.$refs.uToast.show({
					...params,
					complete() {
						params.url && uni.navigateTo({
							url: params.url
						})
					}
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	.box {
		background-color: #F6F6F6;
		height: 100vh;
	}

	.content {
		background-color: #FFFFFF;
		padding-bottom: 30rpx;
	}

	.content-dizhi {
		.content-dizhi-text {
			width: 56rpx;
			height: 40rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 500;
			font-size: 28rpx;
			color: #000000;
			line-height: 40rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			margin-top: 24rpx;
			margin-left: 40rpx;
		}

		.content-dizhi-seek {
			width: 670rpx;
			height: 80rpx;
			background: #F2F2F2;
			border-radius: 20rpx;
			line-height: 80rpx;
			display: flex;
			justify-content: space-between;
			margin-left: 40rpx;
			margin-top: 14rpx;

			.dizhi-seek-text {
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 28rpx;
				color: #999999;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-left: 24rpx;
				white-space: nowrap;
				/* 不换行 */
				overflow: hidden;
				/* 隐藏溢出部分 */
				text-overflow: ellipsis;
				/* 显示省略号 */
			}

			.dizhi-seek-icon-right {
				width: 24rpx;
				height: 24rpx;
				margin-right: 24rpx;
				margin-top: 2rpx;

				image {
					width: 24rpx;
					height: 24rpx;
				}
			}
		}
	}

	.content-number {
		.content-number-text {
			width: 84rpx;
			height: 40rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 500;
			font-size: 28rpx;
			color: #000000;
			line-height: 40rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			margin-top: 24rpx;
			margin-left: 40rpx;
		}

		.content-number-box {
			width: 670rpx;
			height: 80rpx;
			margin-top: 24rpx;
			margin-left: 40rpx;
			background: #F2F2F2;
			border-radius: 20rpx;
			line-height: 80rpx;

			.content-number-box-text {
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 28rpx;
				color: #999999;
				text-align: left;
				margin-left: 24rpx;
				font-style: normal;
				text-transform: none;
				white-space: nowrap;
				/* 不换行 */
				overflow: hidden;
				/* 隐藏溢出部分 */
				text-overflow: ellipsis;
				/* 显示省略号 */
			}
		}
	}

	.new-button {
		width: 670rpx;
		height: 90rpx;
		background: #FFF133;
		border-radius: 50rpx;
		line-height: 90rpx;
		font-weight: 600;
		font-size: 30rpx;
		text-align: center;
		margin-top: 40rpx;
		margin-left: 40rpx;
	}
</style>