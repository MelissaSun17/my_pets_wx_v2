<template>
	<view>
		<u-toast ref="uToast"></u-toast>
		<u-cell-group>
			<u-cell
				:titleStyle="{fontWeight: 500}"
				:title="item.title"
				v-for="(item, index) in list"
				:key="index"
				isLink
				@click="showToast(item)"
			>
			</u-cell>
		</u-cell-group>
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
						title: '成功主题(带图标)',
						message: "庄生晓梦迷蝴蝶",
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
			showToast(params) {
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
<style lang="scss">
	.u-page {
		padding: 0;
	}

	.u-cell-icon {
		width: 36rpx;
		height: 36rpx;
		margin-right: 8rpx;
	}

	.u-cell-group__title__text {
		font-weight: bold;
	}
</style>

