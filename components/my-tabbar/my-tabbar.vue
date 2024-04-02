<template>
	<view class="tabBar">
		<view
		 v-for="(item,index) in tabBar" 
		 :key="item.url" 
		 class="tabbar_item" 
		 :class="{'active':item.url == currentPage}"
		 @click="navTo(item)"
		 >
			<image v-if="item.url == currentPage" :src="item.imgClick" mode=""></image>
			<image v-else :src="item.imgNormal" mode=""></image>
		</view>
	</view>
</template>
 
<script>
	export default {
		props:{
			currentPage:{
				type:String,
				default:'index'
			}
		},
		data() {
			return {
				tabBar:[{
						url:'index/index',
						// text:'首页',
						imgNormal:'../../static/首页已选中@2x.png',
						imgClick:'../../static/首页未选中@2x.png'
					},
					{
						url:'serve/index',
						// text:'分类',
						imgNormal:'../../static/服务已选中@3x.png',
						imgClick:'../../static/服务未选中@3x.png'
						
					},
					{
						url:'news/index',
						// text:'我的',
						imgNormal:'../../static/消息已选中@2x.png',
						imgClick:'../../static/消息未选中@2x.png'
						
					},
					{
						url:'main/index',
						// text:'分类',
						imgNormal:'../../static/我的已选中@2x.png',
						imgClick:'../../static/我的未选中@2x.png'
						
					},]
			};
		},
		created() {
			uni.hideTabBar({})
		},
		computed:{
			
		},
		methods:{
			navTo(item){
				if(item.url !== this.currentPage){
					var isUrl = `/pages/${item.url}`
					const that = this
					uni.switchTab({
						url: isUrl
					})
				} else{
					this.$parent.toTop()
				}
			}
		}
	}
</script>
 
<style lang="scss" scoped>
	  //导航栏设置
		$isRadius:20upx; //左上右上圆角
		$isWidth:100vw; //导航栏宽度
		$isBorder:0px solid white; //边框 不需要则设为0px
		$isBg:white; //背景
	
	  // 选中设置
		$chooseTextColor:#000; //选中时字体颜色
		$chooseBgColor:transparent; //选中时背景颜色 transparent为透明
	
	  //未选中设置
		$normalTextColor:#999; //未选中颜色
	.tabBar{
		
		width: $isWidth;
		height: 150upx;
		position: fixed;
		bottom: 0rpx;
		padding-bottom: 68rpx;
		padding-top: 24rpx;
		left: 0;
		right: 0;
		box-shadow: 0upx 2upx 10upx rgba(89,125,172,.4);
		margin:0 auto;
		z-index: 998;
		background-color: $isBg;
		color: $normalTextColor;
		border-left: $isBorder;
		border-top: $isBorder;
		border-right: $isBorder;
		display: flex;
		justify-content: space-around;
		// border-radius: 80rpx;
		box-sizing: border-box;
		overflow: hidden;
		.tabbar_item{
			width: 25%;
			font-size: 12px;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			&.active{
				border-left: $isBorder;
				border-top: $isBorder;
				background: $chooseBgColor;
				color: $chooseTextColor;
			}
		}
		image{
			width: 150upx;
			height:54upx;
		}
	}
</style>