<template>
	<view class="box">
		<view class="content">
			<view class="content-step">
				<view class="buzou">
					<view class="step1"
						:class="{ 'step': true, 'active': currentStep === 1, 'completed': currentStep >= 1 }"
						@click="setCurrentStep(1)">
						<image src="../../static/分步/选中/1.png" mode=""></image>
					</view>
					<view class="buzou-text">
						详细填写
					</view>
				</view>
				<view class="xuxian">
					<view class="divider"></view>
				</view>
				<view class="buzou">
					<view class="step2" :class="{ 'active': currentStep === 2, 'completed': currentStep >= 2 }"
						@click="setCurrentStep(2)">
						<image v-if="showText2" src="../../static/分步/未选中/2.png" mode=""></image>
						<image v-else src="../../static/分步/选中/2.png" mode=""></image>
					</view>
					<view class="buzou-text2" :style="{ color: showText2 ? 'color: rgba(17, 17, 17, 0.3);' : '#000000' }">
						更多服务
					</view>
				</view>
				<view class="xuxian">
					<view class="divider"></view>
				</view>
				<view class="buzou">
					<view class="step3" :class="{ 'active': currentStep === 3, 'completed': currentStep >= 3 }"
						@click="setCurrentStep(3)">
						<image v-if="showText3" src="../../static/分步/未选中/3.png" mode=""></image>
						<image v-else src="../../static/分步/选中/3.png" mode=""></image>
					</view>
					<view class="buzou-text3" :style="{ color: showText3 ? 'color: rgba(17, 17, 17, 0.3);' : '#000000' }">
						下单预约
					</view>
				</view>
			</view>
			<view class="jianjie">
				<view class="jianjie-left">
					<view class="jianjie-main">
						<view class="jianjie-main-touxiang">
							<image src="../../static/logo.png" mode=""></image>
						</view>
						<view class="jianjie-main-text">
							王小六刘
						</view>
					</view>
					<image class="jianjie-main-img" src="../../static/宠托师.png" mode=""></image>
				</view>
				<view class="jianjie-right">
					<view class="jianjie-fuwu">
						<image class="jianjie-fuwu-img" src="../../static/服务项目.png" mode=""></image>
						<view class="jianjie-fuwu-text">
							上门遛狗
						</view>
					</view>
				</view>
			</view>
			<view class="fuwudizhi">
				<view class="fuwudizhi-top">
					服务地址
				</view>
				<view class="dizhi">
					<view class="dizhi-left">
						<image src="../../static/icon_location@3x.png" mode=""></image>
					</view>
					<view class="dizhi-text">
						徐汇区田林星巴克东南50米
					</view>
					<view class="dizhi-right">
						<image src="../../static/icon_arrow.png" mode=""></image>
					</view>
				</view>
				<view class="dizhi-tishi">
					<view class="dizhi-tishi-icon">
						<image src="../../static/提示/红.png" mode=""></image>
					</view>
					<view class="dizhi-tishitext">
						当前地址不完整，请<text class="underline">完善门牌号信息</text>
					</view>
				</view>
			</view>
			<view class="fuwubaby">
				<view class="fuwubaby-top">
					服务宝贝
				</view>
				<view class="fuwubaby-xinzeng">
					<view class="fuwubaby-img" @click="optFor">
						<view class="img_">
							<image src="../../static/logo.png" mode=""></image>
							<view class="overlay" v-if="overlay">
								<image src="../../static/选择@2x.png" mode=""></image>
							</view>
						</view>
						<view class="text">
							妮妮
						</view>
					</view>
					<view class="fuwubaby-img" @click="optFor">
						<view class="img_">
							<image src="../../static/logo.png" mode=""></image>
							<view class="overlay" v-if="overlay">
								<image src="../../static/选择@2x.png" mode=""></image>
							</view>
						</view>
						<view class="text">
							妮妮
						</view>
					</view>
					<view class="fuwubaby-img" @click="optFor">
						<view class="img_">
							<image src="../../static/logo.png" mode=""></image>
							<view class="overlay" v-if="overlay">
								<image src="../../static/选择@2x.png" mode=""></image>
							</view>
						</view>
						<view class="text">
							妮妮
						</view>
					</view>
					<view class="fuwubaby-img" @click="optFor">
						<view class="img_">
							<image src="../../static/logo.png" mode=""></image>
							<view class="overlay" v-if="overlay">
								<image src="../../static/选择@2x.png" mode=""></image>
							</view>
						</view>
						<view class="text">
							妮妮
						</view>
					</view>
					<view class="fuwubaby-img" @click="optFor">
						<view class="img_">
							<image src="../../static/logo.png" mode=""></image>
							<view class="overlay" v-if="overlay">
								<image src="../../static/选择@2x.png" mode=""></image>
							</view>
						</view>
						<view class="text">
							妮妮
						</view>
					</view>
					<view class="fuwubaby-img">
						<view class="img_">
							<image src="../../static/btn_add@3x.png" mode=""></image>
						</view>
						<view class="text">
							新增宝贝
						</view>
					</view>
				</view>
				<view class="fuwubaby-tishi">
					<view class="fuwubaby-tishi-icon">
						<image src="../../static/提示/灰.png" mode=""></image>
					</view>
					<view class="fuwubaby-tishi-text">
						该宠托师尚未提供猫/小型犬服务，但您也可以发送预约单商榷或<text class="underline">重新搜索宠托师</text>
					</view>
				</view>
			</view>
			<view class="fuwuriqi">
				<u-calendar title="服务日期" rowHeight="100" :maxDate="maxDate" color="#FFD1DB" round="30rpx" :show="show"
					:mode="mode" @confirm="confirm" @close="close"></u-calendar>
				<view class="" @click="show = true">
					<view class="fuwuriqi-top">
						服务日期
					</view>
					<view class="fuwuriqi-shijian">
						<view class="fuwuriqi-shijian-lest">
							<image src="../../static/icon_time.png" mode=""></image>
						</view>
						<view class="fuwuriqi-shijian-text">
							请选择服务日期
						</view>
						<view class="fuwuriqi-shijian-right">
							<image src="../../static/icon_arrow.png" mode=""></image>
						</view>
					</view>
				</view>
				<view class="riqi-tishi">
					<view class="riqi-tishi-icon">
						<image src="../../static/提示/灰.png" mode=""></image>
					</view>
					<view class="riqi-tishi-text">
						您选择的时间可能与该宠托师不匹配，但您也可以发送预约单商榷或<text class="underline">重新搜索宠托师</text>
					</view>
				</view>
				<view class="riqixuanze">
					<view class="riqixuanze-tabs">
						<u-tabs class="custom-tabs" lineColor="#000000" lineHeight="5" lineWidth="30"
							:active="activeTab" :list="list1" @change="changeTab">
						</u-tabs>
					</view>
					<view class="">
						<view v-if="activeTab ==0">
							<view class="tabs-shichang">
								<view class="tabs-shichang-left">
									服务时长
								</view>
								<view class="tongbu" :style="{ backgroundColor: backgroundColor }" v-if="!showTimeList"
									@click="tongbu">
									{{ buttonText }}
								</view>
							</view>
							<view class="tabs-shijian">
								<view class="tabs-shijian-one" :class="{ 'selectedColor': selectedBox === 'box1' }"
									@click="toggleSelection('box1')">
									30分钟
								</view>
								<view class="tabs-shijian-two" :class="{ 'selectedColor': selectedBox === 'box2' }"
									@click="toggleSelection('box2')">
									60分钟
								</view>
							</view>
							<view class="shangmenshijian">
								期望上门时间
							</view>
							<view class="qiwangshijian" @click="goTime" v-if="showTimeList">
								<view class="qiwangshijian-text">
									请选择期望上门时间
								</view>
								<view class="qiwangshijian-icon">
									<image src="../../static/icon_arrow.png" mode=""></image>
								</view>
							</view>
							<view class="shijian-list" v-if="!showTimeList">
								<view class="shijian-list-info" v-for="(item, index) in timeList" :key="index">
									<view class="shijian-list-info-jici">
										{{ item.name }}
									</view>
									<view class="shijian-list-info-time">
										{{ item.time }}
									</view>
									<view class="shijian-list-info-icon">
										<image src="../../static/icon_arrow.png" mode=""></image>
									</view>
								</view>
							</view>
						</view>
						<view v-if="activeTab ==1">
							<text>内容2</text>
						</view>
						<view v-if="activeTab ==2">
							<text>内容3</text>
						</view>
						<view v-if="activeTab ==3">
							<text>内容4</text>
						</view>
					</view>
					<uni-popup ref="popup" background-color="#fff" @change="change">
						<view class="popup-content" :class="{ 'popup-height': type === 'left' || type === 'right' }">
							<view class="shangmen-time-top">
								<view class="shangmen-time-top-text">
									上门时间
								</view>
								<view class="shangmen-time-top-img" @click="guan">
									<image src="../../static/QQ截图20240401171515.png" mode=""></image>
								</view>
							</view>
							<view class="time-xuanze">
								<view class="" v-for="(item,index) in list2" :key="index" @click="toggleColor(index)">
									<view class="time-xuanze-text" :class="{ 'isSelected': isSelected(index) }">
										{{item.name}}
										<view class="kongxian">
											空闲
										</view>
									</view>
								</view>
							</view>
							<view class="open" @click="querenThree"
								:style="{ color: isAnySelected ? '#FF5C7F' : '#D8D8D8 ' }">
								<text>确认</text>
							</view>
						</view>
					</uni-popup>
				</view>
			</view>
			<view class="kong">

			</view>
		</view>
		<view class="btn-bottom">
			<view class="btn" @click="nextStep">
				下一步
			</view>
		</view>
	</view>
</template>

<script>
	const d = new Date()
	const year = d.getFullYear()
	let month = d.getMonth() + 1
	month = month < 10 ? `0${month}` : month
	const date = d.getDate()
	export default {
		data() {
			return {
				overlay: false,
				maxDate: `${year}-${month}-${date + 90}`,
				show: false,
				mode: 'multiple',
				list1: [{
					name: '7月12日',
				}, {
					name: '7月13日',
				}, {
					name: '7月14日'
				}, {
					name: '7月15日'
				}],
				activeTab: 0,
				selectedBox: null, // 用于跟踪当前选中的盒子
				isAnySelected: false,
				selectedIndices: [], // 用于跟踪选中的选项索引
				showTimeList: true,
				showTongBu: false,
				buttonText: "同步到所有天",
				backgroundColor: "white",
				currentStep: 1, // 当前步骤
				showText2: true, // 控制步骤2的文本或图片显示
				showText3: true, // 控制步骤3的文本或图片显示
				list2: [{
						name: '6:00',
					},
					{
						name: '6:30',
					},
					{
						name: '7:00',
					},
					{
						name: '7:30',
					},
					{
						name: '8:00',
					},
					{
						name: '8:30',
					},
					{
						name: '9:00',
					},
					{
						name: '9:30',
					},
					{
						name: '10:00',
					},
					{
						name: '10:30',
					},
					{
						name: '11:00',
					},
					{
						name: '11:30',
					},
					{
						name: '12:00',
					},
					{
						name: '12:30',
					},
					{
						name: '13:00',
					},
					{
						name: '13:30',
					},
					{
						name: '14:00',
					},
					{
						name: '14:30',
					},
					{
						name: '15:00',
					},
					{
						name: '15:30',
					},
					{
						name: '16:00',
					},
					{
						name: '16:30',
					},
					{
						name: '17:00',
					},
					{
						name: '17:30',
					},
				],
				timeList: [{
						name: '第一次：',
						time: '8:00'
					},
					{
						name: '第二次：',
						time: '12:00'
					},
					{
						name: '第三次：',
						time: '16:00'
					}
					// 添加更多时间
				],
			}
		},
		methods: {
			setCurrentStep(step) {
				// 特殊处理第一步，直接跳到第二步
				if (step === 1) {
					this.currentStep = 2;
				} else {
					this.currentStep = step;
				}
			},
			nextStep() {
				if (this.currentStep < 3) {
					this.currentStep++;
					// 如果当前步骤是第二步，则将其状态设置为完成
					if (this.currentStep === 2) {
						this.showText2 = false;
						this.currentStep++;
					}
				} else if (this.currentStep === 3) {
					// 隐藏步骤3文本，显示图片
					this.showText3 = false;
				} else {
					this.currentStep = 1; // 重置到第一步
				}
			},
			tongbu() {
				this.buttonText = "已同步到所有天";
				this.backgroundColor = this.backgroundColor === "white" ? "#B0B0B0 " : "#B0B0B0";
			},
			querenThree() {
				console.log(111);
				this.$refs.popup.close();
				this.showTimeList = false
			},
			guan() {
				this.$refs.popup.close();
			},
			toggleColor(index) {
				const selectedIndex = this.selectedIndices.indexOf(index);
				if (selectedIndex > -1) {
					// 如果已经选中，就取消选中
					this.selectedIndices.splice(selectedIndex, 1);
					this.isAnySelected = this.selectedIndices.length > 0; // 检查是否还有文本被选中
				} else {
					// 如果未选中，就添加到选中列表中
					this.selectedIndices.push(index);
					this.isAnySelected = true; // 没有文本被选中
				}
			},
			isSelected(index) {
				// 判断当前选项是否被选中
				return this.selectedIndices.includes(index);
			},
			goTime() {
				this.toggle('bottom');
			},
			toggle(type) {
				this.type = type
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.popup.open(type)
			},
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			toggleSelection(boxId) {
				if (this.selectedBox === boxId) {
					// 如果点击的是当前已选中的盒子，则取消选中状态
					this.selectedBox = null;
				} else {
					// 选中新的盒子
					this.selectedBox = boxId;
				}
			},
			changeTab(index) {
				this.activeTab = index.index;
				console.log(111);
			},
			optFor() {
				this.overlay = !this.overlay
			},
			aa() {
				console.log(111);
			},
			calendarConfirm(e) {
				this.show = false,
					console.log(e);
			},
			confirm(selectedDates) {
				this.defaultDateMultiple = selectedDates;
				console.log('日历选择：', selectedDates)
				this.show = false,
					this.isColor = true;
			},
			close() {
				console.log(111);
				this.show = false
			},
		}
	}
</script>

<style lang="less" scoped>
	.box {
		height: 100vh;
		background-color: #FFFFFF;

		.btn-bottom {
			background-color: #FFFFFF;
			position: fixed;
			bottom: 0;
			.btn {
				width: 686rpx;
				height: 96rpx;
				background: #D5D5D5;
				border-radius: 48rpx;
				text-align: center;
				line-height: 96rpx;
				margin-top: 32rpx;
				margin-left: 32rpx;
				margin-bottom: 60rpx;
			}
		}

		.buzou {
			width: 120rpx;
			height: 106rpx;
			text-align: center;

			.buzou-text {

				width: 120rpx;
				height: 32rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 24rpx;
				color: #111111;
				line-height: 32rpx;
				font-style: normal;
				margin-top: 18rpx;
			}

			.buzou-text2 {
				width: 120rpx;
				height: 32rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(17, 17, 17, 0.3);
				line-height: 32rpx;
				text-align: center;
				font-style: normal;
				margin-top: 18rpx;
			}

			.buzou-text3 {
				width: 120rpx;
				height: 32rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(17, 17, 17, 0.3);
				line-height: 32rpx;
				text-align: center;
				font-style: normal;
				margin-top: 18rpx;
			}
		}

		.kong {
			height: 230rpx;
		}

		.content-step {
			display: flex;
			margin-left: 60rpx;
			padding-top: 6rpx;

		}

		.step1,
		.step2,
		.step3 {
			
			image {
				width: 56rpx;
				height: 56rpx;
			}
		}

		/* 中间虚线样式 */
		.divider {
			display: inline-block;
			height: 1px;
			width: 70px;
			/* 虚线宽度 */
			border-top: 1px dashed #000;
			/* 虚线样式 */
			vertical-align: middle;
			/* 垂直居中 */
		}

		.isSelected {
			background-color: #FFD1DB !important;
		}

		// /deep/.u-tabs__wrapper__nav{
		// 	background-color: red !important;
		// }
		/deep/.u-tabs__wrapper__nav__item.data-v-0de61367 {
			padding-left: 0 !important;
			font-size: 26rpx !important;
		}

		.selected {
			color: black !important;
			/* 改变你想要的颜色 */
		}

		.selectedColor {
			background-color: #FFD1DB !important;
			color: #000 !important;
		}

		.shangmen-time-top {
			display: flex;
			justify-content: space-between;
			margin-bottom: 38rpx;

			.shangmen-time-top-text {
				width: 224rpx;
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: center;
				font-style: normal;
				margin-left: 264rpx;
				margin-top: 38rpx;
			}

			.shangmen-time-top-img {
				image {
					margin-right: 40rpx;
					margin-top: 40rpx;
					width: 40rpx;
					height: 40rpx;
				}
			}
		}

		.time-xuanze {
			display: flex;
			flex-wrap: wrap;
			margin-left: 40rpx;

			.time-xuanze-text {
				width: 156rpx;
				height: 108rpx;
				border-radius: 16rpx;
				line-height: 108rpx;
				text-align: center;
				background: #F2F2F2;
				margin-right: 16rpx;
				margin-top: 16rpx;
				color: #999999;
				position: relative;

				.kongxian {
					width: 40rpx;
					height: 28rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 400;
					font-size: 20rpx;
					color: #999999;
					line-height: 28rpx;
					text-align: left;
					font-style: normal;
					position: absolute;
					top: 6rpx;
					left: 10rpx;
				}
			}
		}

		.open {
			width: 750rpx;
			text-align: center;
			padding-top: 28rpx;
			border-top: 2rpx solid #EBE9E9;
			margin-top: 72rpx;
		}

		.content {
			background-image: url('../../static/bg@3x.png');
			background-size: 100%;
			background-repeat: no-repeat;

			.content-step {
				height: 106rpx;
			}

			.jianjie {
				display: flex;
				margin-top: 26rpx;

				.jianjie-left {
					width: 316rpx;
					height: 124rpx;
					background: #FFFFFF;
					border-radius: 32rpx;
					border: 2rpx solid #000000;
					margin-right: 28rpx;
					box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
					display: flex;
					line-height: 154rpx;
					margin-left: 40rpx;
					position: relative;

					.jianjie-main {
						display: flex;
						margin-left: 78rpx;

						.jianjie-main-touxiang {
							width: 40rpx;
							height: 40rpx;
							margin-top: 8rpx;

							image {
								width: 40rpx;
								height: 40rpx;
								border-radius: 50rpx;
							}
						}

						.jianjie-main-text {
							width: 130rpx;
							margin-left: 8rpx;
						}
					}

					.jianjie-main-img {
						position: absolute;
						width: 114rpx;
						height: 40rpx;
						top: 0;
						left: 100rpx;

						image {
							width: 114rpx;
							height: 40rpx;
						}
					}
				}

				.jianjie-right {
					width: 316rpx;
					height: 124rpx;
					background: #FFFFFF;
					border-radius: 32rpx;
					border: 2rpx solid #000000;
					box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
					line-height: 154rpx;
					text-align: center;

					.jianjie-fuwu {
						position: relative;

						.jianjie-fuwu-img {
							position: absolute;
							top: 0;
							left: 90rpx;
							width: 136rpx;
							height: 40rpx;

							image {
								width: 136rpx;
								height: 40rpx;
							}
						}
					}
				}
			}

			.fuwudizhi {
				width: 660rpx;
				// height: 288rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				margin-left: 40rpx;
				margin-top: 34rpx;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				padding-bottom: 24rpx;

				.fuwudizhi-top {
					width: 112rpx;
					height: 40rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 600;
					font-size: 28rpx;
					color: #000000;
					line-height: 40rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-left: 32rpx;
					margin-top: 24rpx;
				}

				.dizhi {
					width: 596rpx;
					height: 104rpx;
					background: #F2F2F2;
					border-radius: 16rpx;
					display: flex;
					border-radius: 32rpx;
					margin-top: 16rpx;
					line-height: 104rpx;
					margin-left: 32rpx;

					.dizhi-left {
						width: 40rpx;
						height: 40rpx;
						margin-left: 30rpx;
						margin-right: 2rpx;
						margin-top: 10rpx;

						image {
							width: 40rpx;
							height: 40rpx;
						}
					}

					.dizhi-text {
						width: 480rpx;
					}

					.dizhi-right {
						width: 24rpx;
						height: 24rpx;

						image {
							width: 24rpx;
							height: 24rpx;
						}
					}
				}

				.dizhi-tishi {
					display: flex;
					width: 596rpx;
					height: 64rpx;
					background: rgba(255, 92, 127, 0.12);
					border-radius: 16rpx;
					margin-top: 16rpx;
					margin-left: 32rpx;
					line-height: 64rpx;

					.dizhi-tishi-icon {
						width: 23rpx;
						height: 23rpx;
						margin-left: 18rpx;
						margin-right: 4rpx;

						image {
							width: 23rpx;
							height: 23rpx;
						}
					}

					.dizhi-tishitext {
						font-size: 22rpx;
						color: #FF5C7F;

						.underline {
							text-decoration: underline;
							text-decoration-style: solid;
						}
					}
				}
			}

			.fuwubaby {
				width: 660rpx;
				// height: 362rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				padding-bottom: 24rpx;
				margin-left: 40rpx;
				margin-top: 38rpx;

				.fuwubaby-top {
					width: 112rpx;
					height: 40rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 600;
					font-size: 28rpx;
					color: #000000;
					line-height: 40rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
					margin-left: 32rpx;
				}

				.fuwubaby-xinzeng {
					display: flex;
					flex-wrap: wrap;

					.fuwubaby-img {
						margin-top: 16rpx;
						margin-left: 44rpx;
						width: 104rpx;
						height: 104rpx;
						border-radius: 0rpx 0rpx 0rpx 0rpx;
						margin-bottom: 40rpx;

						.text {
							margin-top: 8rpx;
							width: 104rpx;
							height: 34rpx;
							font-family: PingFang SC, PingFang SC;
							font-weight: 500;
							font-size: 24rpx;
							color: #333333;
							line-height: 28rpx;
							text-align: center;
							font-style: normal;
							text-transform: none;
						}

						image {
							width: 104rpx;
							height: 104rpx;
							border-radius: 100rpx;
						}

						.img_ {
							position: relative;

							.overlay {
								position: absolute;
								right: 0;
								top: 0;

								image {
									width: 40rpx;
									height: 40rpx;
								}
							}
						}
					}
				}

				.fuwubaby-tishi {
					width: 596rpx;
					height: 96rpx;
					background: #F2F2F2;
					border-radius: 16rpx;
					margin-top: 12rpx;
					margin-left: 32rpx;
					display: flex;

					.fuwubaby-tishi-icon {
						width: 28rpx;
						height: 28rpx;
						margin-top: 12rpx;
						margin-left: 20rpx;
						margin-right: 4rpx;

						image {
							width: 28rpx;
							height: 28rpx;
						}
					}

					.fuwubaby-tishi-text {
						font-size: 22rpx;
						margin-top: 16rpx;
						color: #999999;

						.underline {
							text-decoration: underline;
							text-decoration-style: solid;
						}
					}
				}
			}

			.fuwuriqi {
				width: 660rpx;
				// height: 208rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				padding-bottom: 24rpx;
				margin-left: 40rpx;
				margin-top: 42rpx;

				.fuwuriqi-top {
					width: 112rpx;
					height: 40rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 600;
					font-size: 28rpx;
					color: #000000;
					line-height: 40rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-top: 24rpx;
					margin-left: 32rpx;
				}

				.fuwuriqi-shijian {
					margin-top: 16rpx;
					width: 596rpx;
					height: 104rpx;
					margin-left: 32rpx;
					background: #F2F2F2;
					border-radius: 16rpx;
					line-height: 104rpx;
					display: flex;

					.fuwuriqi-shijian-lest {
						margin-top: 8rpx;
						margin-left: 24rpx;
						width: 40rpx;
						height: 40rpx;

						image {
							width: 40rpx;
							height: 40rpx;
						}
					}

					.fuwuriqi-shijian-text {
						margin-left: 8rpx;
						font-size: 28rpx;
						color: #999999;
						width: 480rpx;
					}

					.fuwuriqi-shijian-right {
						width: 24rpx;
						height: 24rpx;

						image {
							width: 24rpx;
							height: 24rpx;
						}
					}
				}
			}

			.riqi-tishi {
				width: 596rpx;
				height: 96rpx;
				background: #F2F2F2;
				border-radius: 16rpx;
				display: flex;
				margin-top: 12rpx;
				margin-left: 32rpx;

				.riqi-tishi-icon {
					width: 28rpx;
					height: 28rpx;
					margin-top: 12rpx;
					margin-left: 20rpx;
					margin-right: 4rpx;

					image {
						width: 28rpx;
						height: 28rpx;
					}
				}

				.riqi-tishi-text {
					font-size: 22rpx;
					margin-top: 16rpx;
					color: #999999;

					.underline {
						text-decoration: underline;
						text-decoration-style: solid;
					}
				}
			}

			.riqixuanze {
				width: 596rpx;
				margin-left: 32rpx;
				margin-top: 40rpx;
				// position: relative;

				.tabs-shichang {
					display: flex;
					justify-content: space-between;
					margin-top: 24rpx;

					.tabs-shichang-left {
						width: 96rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
					}

					.tongbu {
						width: 172rpx;
						height: 48rpx;
						border-radius: 24rpx;
						border: 1rpx solid #CCCCCC;
						text-align: center;
						line-height: 48rpx;
						font-size: 22rpx;
						color: #333333;
					}

					.yitongbu {
						width: 194rpx;
						height: 48rpx;
						background: #F2F2F2;
						border-radius: 24rpx;
						font-size: 22rpx;
						color: #666666;
						text-align: center;
						line-height: 48rpx;
					}
				}

				.tabs-shijian {
					display: flex;

					.tabs-shijian-one {
						width: 160rpx;
						height: 64rpx;
						border-radius: 66rpx;
						background-color: #F2F2F2;
						font-size: 24rpx;
						color: #666666;
						line-height: 64rpx;
						text-align: center;
						margin-top: 16rpx;
					}

					.tabs-shijian-two {
						width: 160rpx;
						height: 64rpx;
						border-radius: 66rpx;
						background-color: #F2F2F2;
						font-size: 24rpx;
						color: #666666;
						line-height: 64rpx;
						text-align: center;
						margin-top: 16rpx;
						margin-left: 16rpx;
					}
				}

				.shangmenshijian {
					width: 144rpx;
					height: 34rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 400;
					font-size: 24rpx;
					color: #000000;
					line-height: 34rpx;
					text-align: left;
					font-style: normal;
					margin-top: 24rpx;
				}

				.qiwangshijian {
					width: 596rpx;
					height: 80rpx;
					background: #F2F2F2;
					border-radius: 20rpx;
					margin-top: 16rpx;
					display: flex;
					justify-content: space-between;
					line-height: 80rpx;

					.qiwangshijian-text {
						font-size: 28rpx;
						color: #999999;
						margin-left: 24rpx;
					}

					.qiwangshijian-icon {
						width: 24rpx;
						height: 24rpx;
						margin-right: 24rpx;

						image {
							width: 24rpx;
							height: 24rpx;
						}
					}
				}

				.shijian-list {
					.shijian-list-info {
						display: flex;
						width: 596rpx;
						height: 80rpx;
						background: #F2F2F2;
						border-radius: 20rpx;
						line-height: 80rpx;
						margin-top: 16rpx;

						.shijian-list-info-jici {
							width: 116rpx;
							height: 40rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 28rpx;
							color: #666666;
							text-align: left;
							font-style: normal;
							text-transform: none;
							margin-left: 24rpx;
						}

						.shijian-list-info-time {
							width: 410rpx;
							height: 40rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 500;
							font-size: 28rpx;
							color: #111111;
							font-style: normal;
							text-transform: none;
						}

						.shijian-list-info-icon {
							width: 24rpx;
							height: 24rpx;

							image {
								width: 24rpx;
								height: 24rpx;
							}
						}
					}
				}
			}

			.btn-bottom {
				background-color: #FFFFFF;

				.btn {
					position: fixed;
					bottom: 40rpx;
					width: 686rpx;
					height: 96rpx;
					background: #D5D5D5;
					border-radius: 48rpx;
					text-align: center;
					line-height: 96rpx;
					margin-top: 32rpx;
					margin-left: 32rpx;
					margin-bottom: 40rpx;
				}
			}

		}
	}
</style>