# chenchuang-tabs 前端仿今日头条 tabs 选项卡tabs标签页，根据文字多少自适应 tab项宽度示例


#### 使用方法 
```使用方法
	
	
<!-- spaceLeft设置tabs间距 v-model：绑定选择序列 tabs: 选择数据 change：切换事件  -->
<chenchuang-tabs spaceLeft="12" v-model="industryTabIndex" :tabs="industryTabs" @change="tabChange"></chenchuang-tabs>
					
				
```

#### HTML代码实现部分
```html

<template>
	<view class="content">

		<!-- chenchuang-tabs组件，根据文字自适应tab项宽度，支持自定义标题栏 -->
		<view style="margin-top:14px; margin-left: 8px; margin-right: 10px;">
			<!-- spaceLeft设置tabs间距 v-model：绑定选择序列 tabs: 选择数据 change：切换事件  -->
			<chenchuang-tabs spaceLeft="12" v-model="industryTabIndex" :tabs="industryTabs"
				@change="tabChange"></chenchuang-tabs>

			<!-- 列表组件 -->
			<CCBProjectList :productList="projectList" @click="goProDetail"></CCBProjectList>
		</view>
	</view>
</template>

<script>
	import CCBProjectList from '@/components/CCProjectList.vue';

	export default {
		components: {

			CCBProjectList

		},
		data() {
			return {
				// 列表数组
				projectList: [],
				industryTabs: [{
						name: '光伏产业'
					},
					{
						name: '新能源车电池'
					},
					{
						name: '食品饮料白酒'
					},
					{
						name: '医疗健康'
					},
					{
						name: '银行金融'
					},
					{
						name: '食品饮料白酒'
					},
					{
						name: '行业七'
					},
					{
						name: '行业八'
					}
				],
				industryTabIndex: 0,

			}
		},
		mounted() {
			this.requestData();
		},
		methods: {

			tabChange() {
				console.log('切换行业类型 =' + this.industryTabIndex);
			},
			requestData() {

				// 模拟请求参数设置
				let reqData = {

					'area': '',
					"pageSize": 10,
					"pageNo": this.curPageNum
				}
				// 模拟请求接口
				this.totalNum = 39;
				this.projectList = [];
				for (let i = 0; i < 10; i++) {

					this.projectList.push({
						'proName': '项目名称' + i,
						'proUnit': '公司名称' + i,
						'area': '广州',
						'proType': '省级项目',
						'stage': '已开工',
						'id': i + ''
					});
				}
			}
		}
	}
</script>

<style>
	page {

		background-color: #f6f6f6;
	}

	.content {
		display: flex;
		flex-direction: column;


	}
</style>


```
