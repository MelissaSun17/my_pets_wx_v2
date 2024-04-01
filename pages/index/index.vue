<template>
	<view class="content">
		<view class="u-page">
			<view class="u-demo-block__content">
				<u-row>
					<view class="content_">
						<view class="content_1">
							<u-col span="12">
								<view class="content_left" @click="gotuoguan">
									<image src="../../static/托管服务-入口@2x.png" mode=""></image>
								</view>
							</u-col>
						</view>
						<view class="content_2">
							<u-col span="12">
								<view class="content_right" @click="goshangmen">
									<image src="../../static/上门服务-入口@2x.png" mode=""></image>
								</view>
							</u-col>
						</view>
					</view>
				</u-row>
				<!-- <u-row>
					<u-col span="12">
						<scroll-view class="scroll-view" scroll-x="true" scroll-y="false">
							<view class="demo-box1">
								<view class="box-one">
									<view class="box-one-img">
										<image
											src="https://s2.best-wallpaper.net/wallpaper/iphone/1710/Two-furry-kittens-look_iphone_750x1334.jpg"
											mode=""></image>
										<view class="box-one-info">
											<text class="text1">哆啦</text>
											<text class="text2">6岁&nbsp;布偶猫&nbsp;已绝育</text>
										</view>
									</view>
								</view>
								<view class="box-one">
									<view class="box-one-img">
										<image
											src="https://s2.best-wallpaper.net/wallpaper/iphone/1710/Two-furry-kittens-look_iphone_750x1334.jpg"
											mode=""></image>
										<view class="box-one-info">
											<text class="text1">哆啦</text>
											<text class="text2">6岁&nbsp;你好啊布偶猫&nbsp;已绝育</text>
										</view>
									</view>
								</view>
								<view class="box-one">
									<view class="box-one-img">
										<image
											src="https://s2.best-wallpaper.net/wallpaper/iphone/1710/Two-furry-kittens-look_iphone_750x1334.jpg"
											mode=""></image>
										<view class="box-one-info">
											<text class="text1">哆啦</text>
											<text class="text2">6岁&nbsp;你好啊布偶猫&nbsp;已绝育</text>
										</view>
									</view>
								</view>
								<view class="box-one">
									<view class="box-one-img">
										<image
											src="https://s2.best-wallpaper.net/wallpaper/iphone/1710/Two-furry-kittens-look_iphone_750x1334.jpg"
											mode=""></image>
										<view class="box-one-info">
											<text class="text1">哆啦</text>
											<text class="text2">6岁&nbsp;你好啊布偶猫&nbsp;已绝育</text>
										</view>
									</view>
								</view>
								</view>
						</scroll-view>
					</u-col>
				</u-row> -->
			</view>
			<!-- <u-row>
				<u-col span="12">
					<view class="demo-box2">
						<view class="demo-box2_img">
							<view class="demo-box2-left" @click="gotuoguan">
								<image src="../../static/微信截图_20240329143245.png" mode=""></image>
							</view>
							<view class="demo-box2-right" @click="goshangmen">
								<image src="../../static/微信截图_20240329143411.png" mode=""></image>
							</view>
						</view>
					</view>
				</u-col>
			</u-row> -->
			<u-row>
				<u-col span="12">
					<view class="demo-box3">
						<view class="feimi-serve">
							<view class="feimi-serve-text">
								<view class="feimi-serve-text-title">
									菲咪服务
								</view>
								<view class="feimi-serve-text-img">
									<image src="../../static/标题尾巴@2x.png" mode=""></image>
								</view>
							</view>
							<view class="feimi-serve-icon">
								<view class="icon-view">
									<view class="icon-view-img">
										<image src="../../static/矩形@2x.png" mode=""></image>
									</view>
									<view class="icon-text">服务介绍</view>
								</view>
								<view class="icon-view">
									<view class="icon-view-img">
										<image src="../../static/编组 31@2x.png" mode=""></image>
									</view>
									<view class="icon-text">基金保障</view>
								</view>
								<view class="icon-view">
									<view class="icon-view-img">
										<image src="../../static/矩形备份@2x.png" mode=""></image>
									</view>
									<view class="icon-text">成为宠托师</view>
								</view>
								<view class="icon-view">
									<view class="icon-view-img">
										<image src="../../static/矩形备份 2@2x.png" mode=""></image>
									</view>
									<view class="icon-text">常见问题</view>
								</view>
							</view>
						</view>
						<view class="pet-trainer">
							<view class="pet-trainer-top">
								<view class="pet-trainer-top-text">
									<view class="pet-trainer-text-left">
										宠托师
									</view>
									<view class="pet-trainer-text-left-img">
										<image src="../../static/标题尾巴@2x.png" mode=""></image>
									</view>
								</view>
								<text class="pet-trainer-text-right">查看更多</text>
							</view>
							<view class="pet-trainer-intro">
								<view class="pet-trainer-intro-bag">

								</view>
								<view class="pet-trainer-intro-list">
									<view class="pet-trainer-intro-list-img">
										<image src="https://pic4.zhimg.com/v2-efd4f4517d5bdb43858a04f7e4ff5f7f_r.jpg"
											mode=""></image>
									</view>
									<view class="pet-trainer-intro-list-img-info">
										<view class="list-img-info-top">
											<view class="list-img-info-top-left">泡泡</view>
											<view class="list-img-info-top-right">
												<text class="text_1">
													距您
												</text>
												<text class="text_2">
													0.8
												</text>
												<text class="text_3">
													km
												</text>
											</view>
										</view>
										<view class="list-img-info-center">
											<text class="text_1">
												养猫10年
											</text>
											<text class="text_2">
												|
											</text>
											<text class="text_3">
												服务过200次
											</text>
										</view>
										<view class="list-img-info-bottom">
											<text class="text_1">
												寄养可接&nbsp;|&nbsp;上门可接
											</text>
											<view class="money">
												<text class="money_text1">￥</text>
												<text class="money_text2">40</text>
												<text class="money_text3">/次起</text>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="pet-trainer-intro">
								<view class="pet-trainer-intro-bag">

								</view>
								<view class="pet-trainer-intro-list">
									<view class="pet-trainer-intro-list-img">
										<image src="https://pic4.zhimg.com/v2-efd4f4517d5bdb43858a04f7e4ff5f7f_r.jpg"
											mode=""></image>
									</view>
									<view class="pet-trainer-intro-list-img-info">
										<view class="list-img-info-top">
											<view class="list-img-info-top-left">泡泡</view>
											<view class="list-img-info-top-right">
												<text class="text_1">
													距您
												</text>
												<text class="text_2">
													0.8
												</text>
												<text class="text_3">
													km
												</text>
											</view>
										</view>
										<view class="list-img-info-center">
											<text class="text_1">
												养猫10年
											</text>
											<text class="text_2">
												|
											</text>
											<text class="text_3">
												服务过200次
											</text>
										</view>
										<view class="list-img-info-bottom">
											<text class="text_1">
												寄养可接&nbsp;|&nbsp;上门可接
											</text>
											<view class="money">
												<text class="money_text1">￥</text>
												<text class="money_text2">40</text>
												<text class="money_text3">/次起</text>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="pet-trainer-intro">
								<view class="pet-trainer-intro-bag">

								</view>
								<view class="pet-trainer-intro-list">
									<view class="pet-trainer-intro-list-img">
										<image src="https://pic4.zhimg.com/v2-efd4f4517d5bdb43858a04f7e4ff5f7f_r.jpg"
											mode=""></image>
									</view>
									<view class="pet-trainer-intro-list-img-info">
										<view class="list-img-info-top">
											<view class="list-img-info-top-left">泡泡</view>
											<view class="list-img-info-top-right">
												<text class="text_1">
													距您
												</text>
												<text class="text_2">
													0.8
												</text>
												<text class="text_3">
													km
												</text>
											</view>
										</view>
										<view class="list-img-info-center">
											<text class="text_1">
												养猫10年
											</text>
											<text class="text_2">
												|
											</text>
											<text class="text_3">
												服务过200次
											</text>
										</view>
										<view class="list-img-info-bottom">
											<text class="text_1">
												寄养可接&nbsp;|&nbsp;上门可接
											</text>
											<view class="money">
												<text class="money_text1">￥</text>
												<text class="money_text2">40</text>
												<text class="money_text3">/次起</text>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="pet-trainer-intro">
								<view class="pet-trainer-intro-bag">

								</view>
								<view class="pet-trainer-intro-list">
									<view class="pet-trainer-intro-list-img">
										<image src="https://pic4.zhimg.com/v2-efd4f4517d5bdb43858a04f7e4ff5f7f_r.jpg"
											mode=""></image>
									</view>
									<view class="pet-trainer-intro-list-img-info">
										<view class="list-img-info-top">
											<view class="list-img-info-top-left">泡泡</view>
											<view class="list-img-info-top-right">
												<text class="text_1">
													距您
												</text>
												<text class="text_2">
													0.8
												</text>
												<text class="text_3">
													km
												</text>
											</view>
										</view>
										<view class="list-img-info-center">
											<text class="text_1">
												养猫10年
											</text>
											<text class="text_2">
												|
											</text>
											<text class="text_3">
												服务过200次
											</text>
										</view>
										<view class="list-img-info-bottom">
											<text class="text_1">
												寄养可接&nbsp;|&nbsp;上门可接
											</text>
											<view class="money">
												<text class="money_text1">￥</text>
												<text class="money_text2">40</text>
												<text class="money_text3">/次起</text>
											</view>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</u-col>
			</u-row>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			gotuoguan(){
				uni.navigateTo({
					url:'/pages/tuoguan/index'
				})
			},
			goshangmen(){
				uni.navigateTo({
					url:'/pages/shangmen/index'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.wrap {
		padding: 12px;
	}
	.content{
		background-color: #FFD1DB;
	}

	.u-demo-block__content {
		display: flex;
		flex-direction: column;
		background-color: #FFD1DB;
		position: relative;
	}

	.content_ {
		z-index: 2;
		display: flex;
		width: 750rpx;
		background-color: #FFD1DB;
		top: 0;

	}

	.content_1 {
		flex: 1;

	}

	.content_2 {
		flex: 1;

	}

	.content_left {
		margin-top: 16rpx;
		height: 360rpx;
		// background-color: #FFD1DB;
		text-align: right;
		z-index: 2;
		image {
			width: 340rpx;
			height: 360rpx;
		}
	}

	.content_right {
		margin-top: 16rpx;
		height: 360rpx;
		// background-color: #FFD1DB;
		z-index: 2;

		image {
			width: 340rpx;
			height: 360rpx;
		}
	}

	.scroll-view {
		background-color: #FFD1DB;
		margin-bottom: 30rpx;
	}

	.demo-box1 {
		display: flex;
		width: 750rpx;
		height: 328rpx;
		border-radius: 8rpx;
		background-color: #FFD1DB;

		.box-one {
			width: 258rpx;
			height: 328rpx;
			position: relative;
			// background: #D8D8D8;
			margin-left: 24rpx;

			.box-one-img {
				width: 230rpx;
				height: 230rpx;
				background: #FFD1DB;
				border-radius: 120rpx 120rpx 60rpx 60rpx;
				margin: 54rpx 16rpx 44rpx 12rpx;

				image {
					width: 230rpx;
					height: 230rpx;
					border-radius: 120rpx 120rpx 60rpx 60rpx;
					border: 4rpx solid black;
				}

				.box-one-info {
					display: flex;
					flex-direction: column;
					width: 196rpx;
					height: 88rpx;
					border: 6rpx solid black;
					border-radius: 20rpx;
					position: absolute;
					left: 24rpx;
					bottom: 6rpx;
					background-color: #ffffff;
					box-shadow: 3rpx 3rpx 13rpx rgba(0, 0, 0, 2);
					overflow: hidden; /* 隐藏溢出部分 */

					.text1 {
						font-size: 32rpx;
						font-weight: 700;
						text-align: center;
						margin-top: 10rpx;
					}

					.text2 {
						width: 190rpx;
						font-size: 20rpx;
						margin-top: 4rpx;
						text-align: center;
						white-space: nowrap; /* 不换行 */
						animation: scroll-left 10s linear infinite; /* 调用动画 */
					}
					@keyframes scroll-left {
					  0% {
					    transform: translateX(100%);
					  }
					  100% {
					    transform: translateX(-100%);
					  }
					}
				}
			}
		}
	}

	.demo-box2 {
		background-color: #FFD1DB;

		.demo-box2_img {
			width: 750rpx;
			background-color: #FFD1DB;
			z-index: 1;
			position: relative;
			height: 160rpx;
			border-radius: 6rpx;
			// margin-top: 30rpx;
			display: flex;

			.demo-box2-left {
				width: 344rpx;
				height: 152rpx;
				margin-left: 40rpx;
				flex: 1;

				image {
					width: 344rpx;
					height: 152rpx;
					border-radius: 0 100rpx 0 0;
				}
			}

			.demo-box2-right {
				position: absolute;
				right: 40rpx;
				width: 344rpx;
				height: 160rpx;
				// border: 1px solid black;
				flex: 1;

				image {
					width: 344rpx;
					height: 160rpx;
					border-radius: 0 0 0 100rpx;
				}
			}
		}
	}



	.demo-box3 {
		z-index: 2;
		top: 375rpx;
		background-image: url('../../static/背景造型@2x.png');
		background-size: 100%;
		 background-repeat: no-repeat; 
		width: 750rpx;
		display: flex;
		flex-direction: column;
		border-top-left-radius: 60rpx;
		/* 左上角 */
		border-top-right-radius: 60rpx;
		/* 右上角 */



		.feimi-serve {
			width: 638rpx;
			height: 220rpx;
			margin-top: 80rpx;
			padding-left: 40rpx;
			padding-right:72rpx ;
			background-color: #FFFFFF;

			.feimi-serve-text {
				display: flex;
				position: relative;
				background-color: #FFFFFF;

				.feimi-serve-text-title {
					width: 176rpx;
					height: 64rpx;
					font-family: HanYiYaKuHei-75W;
					font-weight: normal;
					font-size: 44rpx;
					color: #000000;
					line-height: 64rpx;
					text-align: left;
					font-style: normal;
					font-weight: 800;
				}

				.feimi-serve-text-img {
					position: absolute;
					bottom: 4rpx;
					left: 144rpx;
					width: 44rpx;
					height: 30rpx;

					image {
						width: 45rpx;
						height: 30rpx;
					}
				}
			}

			.feimi-serve-icon {
				width: 606rpx;
				height: 140rpx;
				background-color: #ffffff;
				margin-left: 32rpx;
				display: flex;
				margin-top: 16rpx;

				.icon-view {
					width: 112rpx;
					height: 140rpx;

					.icon-view-img {
						width: 112rpx;
						height: 112rpx;

						image {
							width: 112rpx;
							height: 112rpx;
						}
					}

					.icon-text {
						width: 112rpx;
						text-align: center;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 20rpx;
						color: #4D5154;
						line-height: 24rpx;
						font-style: normal;
					}
				}
			}

			.feimi-serve-icon .icon-view:nth-child(2) {
				margin-left: 52rpx;
				margin-right: 54rpx;
			}

			.feimi-serve-icon .icon-view:nth-child(3) {
				margin-right: 52rpx;
			}
		}

		.pet-trainer {
			padding-top: 40rpx;
			background-color: #ffffff;

			.pet-trainer-top {
				width: 660rpx;
				height: 64rpx;
				margin-left: 40rpx;
				display: flex;
				justify-content: space-between;
				margin-bottom: 30rpx;

				.pet-trainer-top-text {
					width: 154rpx;
					height: 64rpx;
					display: flex;
					position: relative;

					.pet-trainer-text-left {
						width: 132rpx;
						height: 64rpx;
						font-family: HYYakuHei, HYYakuHei;
						font-weight: 700;
						font-size: 44rpx;
						color: #000000;
						line-height: 64rpx;
						text-align: left;
						font-style: normal;
					}

					.pet-trainer-text-left-img {
						position: absolute;
						width: 44rpx;
						height: 30rpx;
						bottom: 10rpx;
						left: 114rpx;

						image {
							width: 44rpx;
							height: 30rpx;
						}
					}
				}

				.pet-trainer-text-right {
					margin-top: 20rpx;
					height: 24rpx;
					width: 96rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 400;
					font-size: 24rpx;
					color: #FF5C7F;
					line-height: 24rpx;
					font-style: normal;
				}
			}

			.pet-trainer-intro {
				flex: 1;
				background-color: #FFFFFF;
				position: relative;
				margin-left: 40rpx;

				.pet-trainer-intro-bag {
					width: 660rpx;
					height: 172rpx;
					background: #000000;
					border-radius: 32rpx;
					border: 2rpx solid #000000;
					position: absolute;
					left: 10rpx;
					top: 22rpx;
					z-index: 1;
				}

				.pet-trainer-intro-list {
					width: 660rpx;
					height: 184rpx;
					border: 1px solid black;
					border-radius: 32rpx;
					display: flex;
					background-color: #FFFFFF;
					position: relative;
					z-index: 2;
					margin-bottom: 34rpx;

					.pet-trainer-intro-list-img {
						width: 132rpx;
						height: 132rpx;
						margin-top: 26rpx;
						margin-left: 24rpx;

						image {
							width: 132rpx;
							height: 132rpx;
							border-radius: 50%;
						}
					}

					.pet-trainer-intro-list-img-info {
						margin-left: 24rpx;
						margin-top: 26rpx;
						width: 448rpx;
						height: 140rpx;

						.list-img-info-top {
							display: flex;
							justify-content: space-between;
							height: 36rpx;

							.list-img-info-top-left {
								width: 130rpx;
								height: 36rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 500;
								font-size: 26rpx;
								color: #000000;
								line-height: 36rpx;
								text-align: left;
								font-style: normal;
							}

							.list-img-info-top-right {
								color: #999999;
								font-size: 22rpx;
								margin-top: 2rpx;

								.text_2 {
									margin-left: 5rpx;
									margin-right: 5rpx;
								}
							}
						}

						.list-img-info-center {
							.text_1 {
								width: 90rpx;
								height: 32rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 22rpx;
								color: #999999;
								line-height: 32rpx;
								text-align: left;
								font-style: normal;
								margin-right: 10rpx;
							}

							.text_2 {
								// width: 20rpx;
								height: 10rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 20rpx;
								color: #999999;
								font-style: normal;
							}

							.text_3 {
								width: 128rpx;
								height: 32rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 22rpx;
								color: #999999;
								line-height: 32rpx;
								text-align: left;
								font-style: normal;
								margin-left: 10rpx;
							}
						}

						.list-img-info-bottom {
							margin-top: 18rpx;
							display: flex;
							justify-content: space-between;

							.text_1 {
								width: 280rpx;
								height: 40rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 600;
								font-size: 28rpx;
								color: #111111;
								line-height: 40rpx;
								text-align: left;
								font-style: normal;
							}

							.money {
								.money_text1 {
									width: 16rpx;
									height: 34rpx;
									font-family: PingFangSC, PingFang SC;
									font-weight: 600;
									font-size: 24rpx;
									color: #FF5C7F;
									line-height: 34rpx;
									text-align: left;
									font-style: normal;
									margin-right: 4rpx;
								}

								.money_text2 {
									width: 48rpx;
									height: 34rpx;
									font-family: PingFangSC, PingFang SC;
									font-weight: 600;
									font-size: 40rpx;
									color: #FF5C7F;
									line-height: 40rpx;
									text-align: left;
									font-style: normal;
									margin-right: 8rpx;
								}

								.money_text3 {
									width: 50rpx;
									height: 34rpx;
									font-family: PingFangSC, PingFang SC;
									font-weight: 500;
									font-size: 20rpx;
									color: #333333;
									line-height: 34rpx;
									text-align: left;
									font-style: normal;
								}
							}
						}
					}
				}
			}
		}
	}
</style>