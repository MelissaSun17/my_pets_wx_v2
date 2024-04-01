<template>
	<view class="box">
		<view class="content">
			<view class="trusteeship">
				<view class="trusteeship-list">
					<view class="trusteeship-list-top">
						<view class="list-top">
							＊
						</view>
						<view class="list-top-text">
							服务项目
						</view>
					</view>
					<own-check class="container" :list="list" color="#666666  " bgColor="#F2F2F2 "
						activeTextColor="#000000" activeBgColor="#FFD1DB" type="1" :btnStyle="btnStyle" fontSize="22rpx"
						@chooseItem="chooseItems">

					</own-check>
					<view class="trusteeship-list-dizhi">
						<view class="list-dizhi">
							＊
						</view>
						<view class="list-dizhi-text">
							服务地址
						</view>
					</view>
					<view class="dingwei" @click="godingwei">
						<view class="dingwei-icon">
							<image src="../../static/QQ截图20240330171750.png" mode=""></image>
						</view>
						<view class="dingwei-text">
							请选择服务地址
						</view>
						<view class="dingwei-icon-right">
							<text>></text>
						</view>
					</view>
				</view>
			</view>
			<view class="fuwu-baby">
				<view class="fuwu-baby-list">
					<view class="fuwu-baby-list-top">
						服务宝贝&nbsp;&nbsp;(多选)
					</view>
					<view class="fuwu-baby-img">
						<view class="container">
							<view class="fuwu-baby-img">
								<view class="fuwu-baby-img-left">
									<view class="_img" :class="{ active: currentTab === 'tab1' }"
										@click="changeTab('tab1')">
										<image v-if="currentTab === 'tab1'" src="../../static/QQ截图20240331115853.png">
										</image>
										<image v-else src="../../static/QQ截图20240331120059.png"></image>
									</view>
								</view>
								<view class="fuwu-baby-img-right">
									<view class="_img" :class="{ active: currentTab === 'tab2' }"
										@click="changeTab('tab2')">
										<image v-if="currentTab === 'tab2'" src="../../static/QQ截图20240331115936.png">
										</image>
										<image v-else src="../../static/QQ截图20240331115754.png"></image>
									</view>
								</view>
							</view>
							<!-- 对应选项卡的内容 -->
							<view class="tab-content">
								<view v-if="currentTab === 'tab1'">
									<view class="tixing">
										狗狗体型
									</view>
									<view class="fuwu-baby-img">
										<view class="fuwu-baby-img-left">
											<view class="_img_" :class="{ active: currentImg === 'img1'}"
												@click="changeImg('img1')">
												<image src="../../static/icon_dog_small@3x.png"></image>
												<view class="text">
													＜5kg
												</view>
											</view>
										</view>
										<view class="fuwu-baby-img-right">
											<view class="_img_" :class="{ active: currentImg === 'img2' }"
												@click="changeImg('img2')">
												<image src="../../static/icon_dog_medium@3x.png"></image>
												<view class="text">5~10kg</view>

											</view>
										</view>
										<view class="fuwu-baby-img-right">
											<view class="_img_" :class="{ active: currentImg === 'img3' }"
												@click="changeImg('img3')">
												<image src="../../static/icon_dog_large@3x.png"></image>
												<view class="text">>10kg</view>
											</view>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
					<view class="time">
						服务时间
					</view>
					<view class="">
						<uni-datetime-picker v-model="datetimerange" type="datetimerange" rangeSeparator="至">
							<view class="fuwu-time">
								<view class="time-icon">
									<image src="../../static/QQ截图20240330181623.png" mode=""></image>
								</view>
								<view class="time-text">
									请选择服务时间
								</view>
								<view class="time-right">
									<text>></text>
								</view>
							</view>
						</uni-datetime-picker>
					</view>
				</view>
			</view>
			<view class="chazhao">
				<view class="chazhao-img">
					<image src="../../static/btn_nor@3x.png" mode=""></image>
				</view>
			</view>

		</view>
	</view>
</template>

<script>
	import ownCheck from '@/components/own-checkBtn/own-check.vue';
	export default {
		components: {
			ownCheck
		},
		data() {
			return {
				currentTab: 'tab1', // 默认显示第一个选项卡
				currentImg: '',
				single: '',
				datetimesingle: '',
				range: ['2021-02-1', '2021-3-28'],
				datetimerange: [],
				start: Date.now() - 1000000000,
				end: Date.now() + 1000000000,
				title: 'Hello',
				btnStyle: {
					"height": "64rpx",
					"line-height": "64rpx",
					"width": "128rpx",
					"border-radius": "32rpx",
					"font-size": '24rpx',
					"font-weight": "600",
				},
				list: [{
						name: "喂食",
						type: 1,
					},
					{
						name: "遛狗",
						type: 2,
					}
				],
			}
		},

		watch: {
			datetimesingle(newval) {
				console.log('单选:', this.datetimesingle);
			},
			range(newval) {
				console.log('范围选:', this.range);
			},
			datetimerange(newval) {
				console.log('范围选:', this.datetimerange);
			}
		},
		mounted() {
			setTimeout(() => {
				this.datetimesingle = Date.now() - 2 * 24 * 3600 * 1000
				this.single = '2021-2-12'
				this.datetimerange = ["2021-07-08 0:01:10", "2021-08-08 23:59:59"]
			}, 3000)
		},

		methods: {
			change(e) {
				this.single = e
				console.log('change事件:', this.single = e);
			},
			changeLog(e) {
				console.log('change事件:', e);
			},
			maskClick(e) {
				console.log('maskClick事件:', e);
			},
			chooseItems(e) {
				console.log(e)
			},
			// 切换选项卡
			changeTab(tab) {
				this.currentTab = tab;
			},
			changeImg(img) {
				this.currentImg = img
			},
			godingwei() {
				uni.navigateTo({
					url: '/pages/dizhi/index'
				})
			},
		}
	}
</script>

<style lang="scss" scoped>
	.box {
		background-color: #FFFFFFF;
	}

	.content {
		background-image: url('../../static/bg@3x.png');
		background-size: 100%;
		background-repeat: no-repeat;
	}

	.trusteeship {
		padding-left: 40rpx;

		.trusteeship-list {
			width: 660rpx;
			height: 358rpx;
			border: 1px solid black;
			border-radius: 32rpx;
			background-color: #FFFFFF;
			box-shadow: 15rpx 15rpx rgba(0, 0, 0, 2);

			.trusteeship-list-top {
				display: flex;

				.list-top {
					width: 18rpx;
					height: 44rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 32rpx;
					color: #FE3A3A;
					line-height: 38rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
					margin-left: 32rpx;
				}

				.list-top-text {
					width: 112rpx;
					height: 40rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 28rpx;
					color: #000000;
					line-height: 33rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 26rpx;
					margin-left: 8rpx;
				}
			}

			.container {
				display: flex;
				margin-top: 16rpx;
				padding-left: 32rpx;
				// background-color: #FE3A3A;

				.rituo {
					width: 128rpx;
					height: 64rpx;
					background: #F2F2F2;
					border-radius: 66rpx 66rpx 66rpx 66rpx;
					text-align: center;
					line-height: 64rpx;
					margin-left: 32rpx;
					margin-right: 24rpx;
				}

				.jiyang {
					width: 128rpx;
					height: 64rpx;
					background: #F2F2F2;
					border-radius: 66rpx 66rpx 66rpx 66rpx;
					text-align: center;
					line-height: 64rpx;
				}
			}

			.trusteeship-list-dizhi {
				display: flex;

				.list-dizhi {
					width: 18rpx;
					height: 44rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 32rpx;
					color: #FE3A3A;
					line-height: 38rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
					margin-left: 32rpx;
				}

				.list-dizhi-text {
					width: 112rpx;
					height: 40rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 28rpx;
					color: #000000;
					line-height: 33rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 26rpx;
					margin-left: 8rpx;
				}
			}

			.dingwei {
				display: flex;
				width: 596rpx;
				height: 80rpx;
				background: rgba(255, 209, 219, 0.5);
				border-radius: 16rpx 16rpx 16rpx 16rpx;
				margin-left: 32rpx;
				margin-top: 16rpx;

				.dingwei-icon {
					// width: 32rpx;
					// height: 32rpx;
					width: 60rpx;
					height: 60rpx;
					margin-left: 20rpx;
					margin-top: 10rpx;
					background: rgba(255, 255, 255, 0);
					border-radius: 0rpx 0rpx 0rpx 0rpx;

					image {
						width: 60rpx;
						height: 60rpx;
					}
				}

				.dingwei-text {
					width: 294rpx;
					height: 32rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 24rpx;
					color: #666666;
					line-height: 32rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
				}

				.dingwei-icon-right {
					width: 24rpx;
					height: 24rpx;
					border-radius: 0rpx 0rpx 0rpx 0rpx;
					margin-left: 182rpx;
					margin-top: 16rpx;
				}
			}
		}
	}

	.fuwu-baby {
		padding-left: 40rpx;
		margin-top: 34rpx;



		.fuwu-baby-list {
			width: 660rpx;
			background: #FFFFFF;
			border-radius: 32rpx 32rpx 32rpx 32rpx;
			border: 2rpx solid #000000;
			background-color: #FFFFFF;
			box-shadow: 15rpx 15rpx rgba(0, 0, 0, 2);

			.fuwu-baby-list-top {
				width: 224rpx;
				height: 40rpx;
				font-family: PingFang SC, PingFang SC;
				font-weight: 600;
				font-size: 28rpx;
				color: #000000;
				line-height: 33rpx;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-left: 32rpx;
				margin-top: 24rpx;
			}

			.fuwu-baby-img {
				display: flex;
				margin-top: 16rpx;

				.fuwu-baby-img-left {
					margin-right: 16rpx;
					width: 144rpx;
					height: 144rpx;
					margin-left: 32rpx;
					background: #F2F2F2;
					border-radius: 16rpx 16rpx 16rpx 16rpx;

					._img {
						width: 144rpx;
						height: 144rpx;

						image {
							width: 144rpx;
							height: 144rpx;
						}
					}

					.fuwu-baby-img-left-text {
						width: 48rpx;
						height: 32rpx;
						font-family: PingFang SC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #666666;
						line-height: 32rpx;
						font-style: normal;
						text-transform: none;
						margin-left: 48rpx;
					}
				}

				.fuwu-baby-img-right {
					width: 144rpx;
					height: 144rpx;
					background: #F2F2F2;
					text-align: center;
					border-radius: 16rpx 16rpx 16rpx 16rpx;
					margin-right: 16rpx;

					._img {
						width: 144rpx;
						height: 144rpx;

						image {
							width: 144rpx;
							height: 144rpx;
						}
					}

					.fuwu-baby-img-right-text {
						width: 48rpx;
						height: 32rpx;
						font-family: PingFang SC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #666666;
						line-height: 32rpx;
						text-align: center;
						font-style: normal;
						text-transform: none;
						margin-left: 48rpx;
					}
				}
			}

			.time {
				width: 112rpx;
				height: 40rpx;
				font-family: PingFang SC, PingFang SC;
				font-weight: 600;
				font-size: 28rpx;
				color: #000000;
				line-height: 33rpx;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-left: 32rpx;
				margin-top: 40rpx;
			}

			.fuwu-time {
				display: flex;
				width: 596rpx;
				height: 80rpx;
				background: rgba(255, 209, 219, 0.5);
				border-radius: 16rpx 16rpx 16rpx 16rpx;
				margin-left: 32rpx;
				margin-top: 16rpx;
				margin-bottom: 32rpx;

				.time-icon {
					width: 32rpx;
					height: 32rpx;
					margin-left: 20rpx;
					margin-top: 24rpx;
					background: rgba(255, 255, 255, 0);
					border-radius: 0rpx 0rpx 0rpx 0rpx;

					image {
						width: 32rpx;
						height: 32rpx;
					}
				}

				.time-text {
					width: 294rpx;
					height: 32rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 24rpx;
					color: #000000;
					line-height: 32rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
					margin-left: 16rpx;
				}

				.time-right {
					width: 24rpx;
					height: 24rpx;
					border-radius: 0rpx 0rpx 0rpx 0rpx;
					margin-left: 182rpx;
					margin-top: 16rpx;
				}
			}
		}
	}

	._img_ {
		width: 144rpx;
		height: 144rpx;
		border-radius: 0rpx 0rpx 0rpx 0rpx;
		background-color: #F2F2F2;
		border-radius: 16rpx;
		text-align: center;

		image {
			width: 88rpx;
			height: 88rpx;
			margin-top: 8rpx;
		}

		.text {
			width: 144rpx;
			height: 32rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 400;
			font-size: 24rpx;
			color: #666666;
			line-height: 32rpx;
			text-align: center;
		}
	}
	.active {
	    background-color: #FFD1DB;
	}
	.tixing{
		width: 112rpx;
		height: 40rpx;
		font-family: PingFang SC, PingFang SC;
		font-weight: 600;
		font-size: 28rpx;
		color: #000000;
		line-height: 33rpx;
		text-align: left;
		font-style: normal;
		text-transform: none;
		margin-left: 32rpx;
		margin-top: 40rpx;
		margin-bottom: 16rpx;
	}

	.chazhao {
		width: 690rpx;
		height: 150rpx;
		margin-left: 20rpx;
		margin-top: 24rpx;

		.chazhao-img {
			width: 720rpx;
			height: 150rpx;

			image {
				width: 720rpx;
				height: 150rpx;
			}
		}
	}
</style>