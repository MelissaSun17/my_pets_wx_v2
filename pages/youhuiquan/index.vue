<template>
	<view class="box">
		<view class="content">
			<view class="quantity">
				可使用优惠券  3张
			</view>
			<view class="quan" @click="toggleCollapse">
				<view class="toubiao">
					<image src="../../static/抵扣券-角标@2x.png" mode=""></image>
				</view>
				<view class="quan-left">
					<view class="quan-left-money">
						<view class="money-left">
							￥
						</view>
						<view class="money-right">
							50
						</view>
					</view>
					<view class="quan-left-text">
						无门槛
					</view>
				</view>
				<view class="quan-middle">
					<view class="text1">
						菲咪抵扣券
					</view>
					<view class="text2">
						所有服务均可使用
					</view>
					<view class="text3">
						有效期截止2026-02-11
					</view>
				</view>
				<view class="quan-icon">
					<image :src="collapsed ? '../../static/选择框-未选择@3x.png' : '../../static/编组 3@3x1.png'" mode=""></image>
				</view>
			</view>
			<view class="quan" @click="toggleCollapse2">
				<view class="toubiao">
					<image src="../../static/满减券-角标@2x.png" mode=""></image>
				</view>
				<view class="quan-left">
					<view class="quan-left-money">
						<view class="money-left">
							￥
						</view>
						<view class="money-right">
							50
						</view>
					</view>
					<view class="quan-left-text2">
					  满100可用
					</view>
				</view>
				<view class="quan-middle">
					<view class="text1">
						菲咪抵扣券
					</view>
					<view class="text2">
						所有服务均可使用
					</view>
					<view class="text3">
						有效期截止2026-02-11
					</view>
				</view>
				<view class="quan-icon">
					<image :src="collapsed2 ? '../../static/选择框-未选择@3x.png' : '../../static/编组 3@3x1.png'" mode=""></image>
				</view>
			</view>
			<view class="zhekouquan" @click="toggleCollapse3">
				<view class="toubiao">
					<image src="../../static/抵扣券-角标@2x.png" mode=""></image>
				</view>
				<view class="quan-left">
					<view class="quan-left-money">
						<view class="money-left">
							7.8
						</view>
						<view class="money-right">
							折
						</view>
					</view>
				</view>
				<view class="quan-middle">
					<view class="text1">
						菲咪抵扣券
					</view>
					<view class="text2">
						所有服务均可使用
					</view>
					<view class="text3">
						有效期截止2026-02-11
					</view>
				</view>
				<view class="quan-icon">
					<image :src="collapsed3 ? '../../static/选择框-未选择@3x.png' : '../../static/编组 3@3x1.png'" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				collapsed: true,
				collapsed2: true,
				collapsed3: true,
			}
		},
		methods:{
			toggleCollapse() {
				this.collapsed = !this.collapsed;
			},
			toggleCollapse2() {
				this.collapsed2 = !this.collapsed2;
			},
			toggleCollapse3() {
				this.collapsed3 = !this.collapsed3;
			},
		}
	}
</script>

<style lang="less" scoped>
	.box{
		background-color: #F6F6F6;
		height: 100vh;
		.content{
			.quantity{
				height: 40rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 500;
				font-size: 28rpx;
				color: #111111;
				line-height: 40rpx;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-left: 40rpx;
				padding-top: 24rpx;
			}
			.zhekouquan{
				width: 686rpx;
				height: 208rpx;
				background-image: url('../../static/优惠券-背景@3x.png');
				background-size: 100%;
				background-repeat: no-repeat;
				margin-left: 32rpx;
				margin-top: 24rpx;
				display: flex;
				position: relative;
				.toubiao{
					position: absolute;
					top: 0;
					left: 0;
					width: 104rpx;
					height: 40rpx;
					background: #FF5C7F;
					border-radius: 24rpx 0rpx 32rpx 0rpx;
					image{
						width: 104rpx;
						height: 40rpx;
					}
				}
				.quan-left{
					.quan-left-money{
						height: 94rpx;
						display: flex;
						margin-top: 42rpx;
						margin-left: 32rpx;
						.money-left{
							color: #FF476E;
							margin-top: 20rpx;
							font-weight: 600;
							margin-right: 14rpx;
							font-size: 70rpx;
						}
						.money-right{
							font-family: PingFangSC, PingFang SC;
							font-weight: 600;
							color: #FF476E;
							text-align: right;
							margin-top: 56rpx;
						}
					}
					.quan-left-text{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 68rpx;
					}
					.quan-left-text2{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 48rpx;
					}
				}
				.quan-middle{
					margin-left: 80rpx;
					.text1{
						height: 44rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 32rpx;
						color: #000000;
						line-height: 44rpx;
						text-align: left;
						font-style: normal;
						text-transform: none;
						margin-top: 28rpx;
					}
					.text2{
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						text-transform: none;
						margin-top: 4rpx;
						
					}
					.text3{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-top: 46rpx;
					}
				}
				.quan-icon{
					margin-left: 100rpx;
					margin-top: 80rpx;
					width: 40rpx;
					height: 40rpx;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
			}
			.quan{
				width: 686rpx;
				height: 208rpx;
				background-image: url('../../static/优惠券-背景@3x.png');
				background-size: 100%;
				background-repeat: no-repeat;
				margin-left: 32rpx;
				margin-top: 24rpx;
				display: flex;
				// justify-content: space-between;
				position: relative;
				.toubiao{
					position: absolute;
					top: 0;
					left: 0;
					width: 104rpx;
					height: 40rpx;
					background: #FF5C7F;
					border-radius: 24rpx 0rpx 32rpx 0rpx;
					image{
						width: 104rpx;
						height: 40rpx;
					}
				}
				.quan-left{
					.quan-left-money{
						height: 94rpx;
						display: flex;
						margin-top: 42rpx;
						margin-left: 32rpx;
						.money-left{
							color: #FF476E;
							margin-top: 40rpx;
							font-weight: 600;
							margin-right: 14rpx;
						}
						.money-right{
							font-family: PingFangSC, PingFang SC;
							font-size: 70rpx;
							font-weight: 600;
							color: #FF476E;
							text-align: right;
						}
					}
					.quan-left-text{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 68rpx;
					}
					.quan-left-text2{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 48rpx;
					}
				}
				.quan-middle{
					margin-left: 80rpx;
					.text1{
						height: 44rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 32rpx;
						color: #000000;
						line-height: 44rpx;
						text-align: left;
						font-style: normal;
						text-transform: none;
						margin-top: 28rpx;
					}
					.text2{
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						text-transform: none;
						margin-top: 4rpx;
						
					}
					.text3{
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-top: 46rpx;
					}
				}
				.quan-icon{
					margin-left: 120rpx;
					margin-top: 80rpx;
					width: 40rpx;
					height: 40rpx;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
			}
		}
	}
</style>