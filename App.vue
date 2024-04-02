<!-- <teleport>
	'<view>
		<custom-tab-bar></custom-tab-bar>
	</view>'
</teleport> -->
<script>
	// import customTabBar from 'pages/tabnav/index.vue'
	export default {
		// components: {
		// 	customTabBar,
		// },
		onLaunch: function() {
			console.log('App Launch')
			// uni.hideTabBar()
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>