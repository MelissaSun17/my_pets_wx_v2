<!-- components/CustomTabBar.vue -->
<template>
	<div class="custom-tab-bar">
		<div class="tab-item" @click="switchTab('home')">首页</div>
		<div class="tab-item" @click="switchTab('serve')">首页</div>
		<div class="tab-item" @click="switchTab('serve')">首页</div>
		<div class="tab-item" @click="switchTab('serve')">首页</div>
	</div>
</template>

<script>
	export default {
		methods: {
			switchTab(tabName) {
				if (tabName === 'home') {
					uni.navigateTo({
						url: '/pages/index/index' // 跳转到首页页面
					});
				} else if (tabName === 'serve') {
					uni.navigateTo({
						url: '/pages/serve/index' // 跳转到我的页面
					});
				}
			}
		}
	}
</script>
<style scoped>
	.custom-tab-bar {
		display: flex;
		justify-content: space-around;
		align-items: center;
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		height: 50px;
		background-color: #fff;
	}

	.tab-item {
		flex: 1;
		text-align: center;
	}
</style>