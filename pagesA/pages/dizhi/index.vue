<template>
	<view class="content">
		<view class="search">
			<view class="search-box">
				<view class="sousuo" @click="aa">
					<uni-search-bar radius="100" placeholder="搜索地址" clearButton="none" cancelButton="none"
						@confirm="search" />
				</view>
				<view class="btn" @click="address">
					<text>
						新增地址
					</text>
				</view>
			</view>
			<view class="" v-show="isComponent1Visible">
				<view class="dangqian">
					当前定位
				</view>
				<view class="dizhi">
					<view class="dizhi-img">
						<image src="../../../static/icon_location@3x.png" mode=""></image>
					</view>
					<view class="dizhi-text" @click="selectAddress">
						徐汇区田林星巴克东南50米
					</view>
					<view class="dizhi-right">
						重新定位
					</view>
				</view>
			</view>
		</view>
		<view class="main-dizhi" v-show="isComponent2Visible">
			<view class="main-dizhi-list">
				<view class="dizhi_list">
					<view class="main-dizhi-list-text2">
						徐汇区田林星巴克东南50米
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
						徐汇区田林星巴克东南50米
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
						徐汇区田林星巴克东南50米
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
		<view class="main-dizhi" v-show="isComponent1Visible">
			<view class="main-dizhi-top">
				我的地址
			</view>
			<u-swipe-action>
				<u-swipe-action-item
				  :options="options1"
				>
				  <view class="swipe-action u-border-top u-border-bottom">
				    <view class="swipe-action__content">
				      <view class="main-dizhi-list">
				      	<view class="main-dizhi-list-text">
				      		徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
				      	</view>
				      	<view class="main-dizhi-list-img" @click="redact">
				      		<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				      	</view>
				      </view>
				    </view>
				  </view>
				</u-swipe-action-item>
			</u-swipe-action>
			<u-swipe-action>
				<u-swipe-action-item
				  :options="options1"
				>
				  <view class="swipe-action u-border-top u-border-bottom">
				    <view class="swipe-action__content">
				      <view class="main-dizhi-list">
				      	<view class="main-dizhi-list-text">
				      		徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
				      	</view>
				      	<view class="main-dizhi-list-img" @click="redact">
				      		<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				      	</view>
				      </view>
				    </view>
				  </view>
				</u-swipe-action-item>
			</u-swipe-action>
			<u-swipe-action>
				<u-swipe-action-item
				  :options="options1"
				>
				  <view class="swipe-action u-border-top u-border-bottom">
				    <view class="swipe-action__content">
				      <view class="main-dizhi-list">
				      	<view class="main-dizhi-list-text">
				      		徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
				      	</view>
				      	<view class="main-dizhi-list-img" @click="redact">
				      		<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				      	</view>
				      </view>
				    </view>
				  </view>
				</u-swipe-action-item>
			</u-swipe-action>
			<!-- <view class="main-dizhi-list">
				<view class="main-dizhi-list-text">
					徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
				</view>
				<view class="main-dizhi-list-img">
					<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				</view>
			</view>
			<view class="main-dizhi-list">
				<view class="main-dizhi-list-text">
					徐汇区田林星巴克东南50米
				</view>
				<view class="main-dizhi-list-img">
					<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				</view>
			</view>
			<view class="main-dizhi-list">
				<view class="main-dizhi-list-text">
					徐汇区田林星巴克东南50米
				</view>
				<view class="main-dizhi-list-img">
					<image src="../../../static/QQ截图20240331223328.png" mode=""></image>
				</view>
			</view> -->
		</view>
		<view class="fujin-dizhi" v-show="isComponent1Visible">
			<view class="fujin-dizhi-top">
				附近地址
			</view>
			<view class="fujin-dizhi-list">
				<view class="fujin-dizhi-list-text">
					徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米徐汇区田林星巴克东南50米
				</view>
			</view>
			<view class="fujin-dizhi-list">
				<view class="fujin-dizhi-list-text">
					徐汇区田林星巴克东南50米
				</view>
			</view>
			<view class="fujin-dizhi-list">
				<view class="fujin-dizhi-list-text">
					徐汇区田林星巴克东南50米
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				isComponent1Visible: true, 
				isComponent2Visible: false, // 控制第二个组件的显示状态
				options1: [{
				    text: '删除'
				}]
			}
		},
		methods: {
			//编辑地址
			redact(){
				uni.navigateTo({
					url:('/pagesA/pages/dizhi/redact_index')
				})
				console.log(111);
			},
			//新增地址
			address(){
				uni.navigateTo({
					url:('/pagesA/pages/newDiZhi/index')
				})
			},
			selectAddress() {
				uni.navigateBack({
					delta: 1,
					success: function() {
						var pages = getCurrentPages();
						var prevPage = pages[pages.length - 1]; // 上一个页面
						prevPage.changeColor(); // 触发修改颜色的操作
					}
				});
			},
			search(){
				console.log(111);
			},
			aa(){
				 this.isComponent1Visible = !this.isComponent1Visible;
				  this.isComponent2Visible = !this.isComponent2Visible;
				console.log(111);
			}
		}
	}
</script>

<style lang="less" scoped>
	/deep/.u-swipe-action-item__right__button__wrapper.data-v-2fea6ae7{
		background-color: #FE3A3A !important;
		border: none !important;
	}
	.content {
		background-color: #F6F6F6;
		height: 100vh;
	}
	.dizhi_list{
		padding-left: 40rpx;
		.main-dizhi-list-text2{
			// width: 342rpx;
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
		}
		.main-dizhi-list-text3{
			// width: 284rpx;
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
		}
	}
	.main-dizhi-list-mi{
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
	.search {
		background-color: #FFFFFF;

		.search-box {
			display: flex;

			.sousuo {
				width: 540rpx;
				height: 72rpx;
				margin-left: 20rpx;
			}

			.btn {
				margin-top: 20rpx;
				width: 168rpx;
				height: 72rpx;
				margin-left: 8rpx;
				background: rgba(255, 209, 219, 0.8);
				border-radius: 102rpx 102rpx 102rpx 102rpx;

				text {
					width: 104rpx;
					height: 72rpx;
					font-family: PingFang SC, PingFang SC;
					font-weight: 600;
					font-size: 26rpx;
					color: #000000;
					line-height: 72rpx;
					text-align: left;
					font-style: normal;
					text-transform: none;
					margin-left: 32rpx;
				}
			}
		}
	}

	.dangqian {
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
		margin-top: 48rpx;
		margin-bottom: 28rpx;
	}

	.dizhi {
		padding-bottom: 36rpx;
		margin-left: 40rpx;
		display: flex;

		.dizhi-img {
			width: 40rpx;
			height: 40rpx;
			// background: #FFFFFF;
			border-radius: 0rpx 0rpx 0rpx 0rpx;
			opacity: 0.5;

			image {
				width: 40rpx;
				height: 40rpx;
			}
		}

		.dizhi-text {
			width: 532rpx;
			height: 32rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 500;
			font-size: 28rpx;
			color: #000000;
			line-height: 32rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			margin-left: 8rpx;
			margin-top: 4rpx;
			white-space: nowrap;
			/* 不换行 */
			animation: scroll-left 10s linear infinite;
			/* 调用动画 */
		}

		.dizhi-right {
			width: 112rpx;
			height: 32rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 400;
			font-size: 28rpx;
			color: #FF5C7F;
			line-height: 32rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			// margin-left: 168rpx;
			margin-top: 4rpx;
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

			.main-dizhi-list-text {
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
				margin-top: 48rpx;
				margin-left: 40rpx;
				white-space: nowrap;
				white-space: nowrap;
				/* 不换行 */
				overflow: hidden;
				/* 隐藏溢出部分 */
				text-overflow: ellipsis;
				/* 显示省略号 */
			}

			.main-dizhi-list-img {
				width: 28rpx;
				height: 28rpx;
				background: #FFFFFF;
				border-radius: 0rpx 0rpx 0rpx 0rpx;
				margin-top: 48rpx;
				margin-right: 56rpx;

				image {
					width: 28rpx;
					height: 28rpx;
				}
			}
		}
	}

	.fujin-dizhi {
		background-color: #FFFFFF;
		margin-top: 16rpx;

		.fujin-dizhi-top {
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

		.fujin-dizhi-list {
			display: flex;
			justify-content: space-between;
			padding-bottom: 48rpx;
			border-bottom: 1rpx solid #EBE9E9;

			.fujin-dizhi-list-text {
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
				margin-top: 48rpx;
				margin-left: 40rpx;
				white-space: nowrap;
				/* 不换行 */
				overflow: hidden;
				/* 隐藏溢出部分 */
				text-overflow: ellipsis;
				/* 显示省略号 */
			}
		}
	}
</style>