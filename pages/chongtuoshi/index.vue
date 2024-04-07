<template>
	<view class="box">
		<u-picker :show="show" :columns="columns" @confirm="confirm" @cancel="cancel"></u-picker>
		<view class="tabs">
			<view class="paixu" @click="show = true">
				排序
				<image src="../../static/QQ截图20240403141954.png" mode=""></image>
			</view>
			<view class="chongwu" type="primary" @click="show2 = true">
				宠物
				<image src="../../static/QQ截图20240403141954.png" mode=""></image>
			</view>
			<!-- <uni-popup ref="popup" background-color="#fff" @change="change">

			</uni-popup> -->
			<u-calendar title="服务日期" rowHeight="100" :maxDate="maxDate" color="#FFD1DB" round="30rpx" :show="show3"
				:mode="mode" @confirm="conshijian" @close="closes"></u-calendar>
			<view class="shijian" @click="show3 = true">
				时间
				<image src="../../static/QQ截图20240403141954.png" mode=""></image>
			</view>
			<u-popup :show="show4" @open="open" :round="50" :safeAreaInsetBottom="true">
				<scroll-view class="color-scroll" scroll-y>
				<view class="fuwu_xiangmu">
					服务项目
				</view>
				<view class="fuwu_xiangmu_list">
					<view class="list-radio">
						<view class="radio-text">
							<view class="radio-text-left">
								<view class="text" :class="{ active: currentTabText === 'xuanzhe1' }"
									@click="changeTabText('xuanzhe1')">
									<text v-if="currentTabText === 'xuanzhe1'">
										上门遛狗
									</text>
									<text v-else>上门遛狗</text>
								</view>
							</view>
							<view class="radio-text-left">
								<view class="text" :class="{ active: currentTabText === 'xuanzhe2' }"
									@click="changeTabText('xuanzhe2')">
									<text v-if="currentTabText === 'xuanzhe2'">
										上门喂食
									</text>
									<text v-else>
										上门喂食
									</text>
								</view>
							</view>
							<view class="radio-text-right">
								<view class="text" :class="{ active: currentTabText === 'xuanzhe3' }"
									@click="changeTabText('xuanzhe3')">
									<text v-if="currentTabText === 'xuanzhe3'">
										寄养
									</text>
									<text v-else>
										寄养
									</text>
								</view>
							</view>
							<view class="radio-text-right">
								<view class="text" :class="{ active: currentTabText === 'xuanzhe4' }"
									@click="changeTabText('xuanzhe4')">
									<text v-if="currentTabText === 'xuanzhe4'">
										日托
									</text>
									<text v-else>
										日托
									</text>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="fuwu_pingfen">
					评分
				</view>
				<view class="fuwu_xiangmu_list">
					<view class="list-radio">
						<view class="radio-text">
							<view class="radio-text-left">
								<view class="text" :class="{ active: currentTabText2 === 'xuanzhe5' }"
									@click="changeTabText2('xuanzhe5')">
									<text v-if="currentTabText2 === 'xuanzhe5'">
										不限
									</text>
									<text v-else>不限</text>
								</view>
							</view>
							<view class="radio-text-left">
								<view class="text" :class="{ active: currentTabText2 === 'xuanzhe6' }"
									@click="changeTabText2('xuanzhe6')">
									<text v-if="currentTabText2 === 'xuanzhe6'">
										5分以上
									</text>
									<text v-else>
										5分以上
									</text>
								</view>
							</view>
							<view class="radio-text-right">
								<view class="text" :class="{ active: currentTabText2 === 'xuanzhe7' }"
									@click="changeTabText2('xuanzhe7')">
									<text v-if="currentTabText2 === 'xuanzhe7'">
										4分以上
									</text>
									<text v-else>
										4分以上
									</text>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="juli">
					<view class="juli_top">
						<view class="juli_left">
							距离
						</view>
						<view class="juli_right">
							30km以内
						</view>
					</view>
					<view class="container">
						<view class="container_flex">
							<view class="progress-wrapper">
								<view class="progress-bar">
									<view class="progress-left" :style="{width: leftWidth + '%'}"></view>
									<view class="progress-right" :style="{width: rightWidth + '%'}"></view>
									<view class="thumb left" :style="{left: leftPosition + '%'}"></view>
									<view class="thumb right" :style="{left: rightPosition + '%'}"></view>
								</view>
							</view>
							<view class="progress-label">30km</view>
						</view>
						<view class="container_btn">
							<view class="btn" :class="{ 'selected1': isSelected(0, 1) }" @click="chage(0,1)">1km内</view>
							<view class="btn" :class="{ 'selected1': isSelected(0, 3) }" @click="chage(0,3)">3km内</view>
							<view class="btn" :class="{ 'selected1': isSelected(0, 5) }" @click="chage(0,5)">5km内</view>
							<view class="btn" :class="{ 'selected1': isSelected(0, 10) }" @click="chage(0,10)">10km内</view>
						</view>
					</view>
				</view>
				<view class="jiage">
					<view class="jiage_top">
						<view class="jiage_left">
							价格
						</view>
						<view class="jiage_right">
							￥150以内
						</view>
					</view>
				</view>
				<view class="container">
					<view class="container_flex">
						<view class="progress-wrapper">
							<view class="progress-bar">
								<view class="progress-left" :style="{width: leftWidth2 + '%'}"></view>
								<view class="progress-right" :style="{width: rightWidth2 + '%'}"></view>
								<view class="thumb left" :style="{left: leftPosition2 + '%'}"></view>
								<view class="thumb right" :style="{left: rightPosition2 + '%'}"></view>
							</view>
						</view>
						<view class="progress-label">￥150</view>
					</view>
					<view class="container_btn2">
						<view class="btn" :class="{ 'selected2': isSelected2(0, 150) }" @click="chage2(0,150)">￥150以下</view>
						<view class="btn" :class="{ 'selected2': isSelected2(50,70) }" @click="chage2(50,70)">￥50-￥70</view>
						<view class="btn" :class="{ 'selected2': isSelected2(70,90) }" @click="chage2(70,90)">￥70-￥90</view>
						<view class="btn" :class="{ 'selected2': isSelected2(0,90) }" @click="chage2(0,90)">￥90以下</view>
					</view>
				</view>
				<view class="jingyan">
					<view class="jingyan_top">
						<view class="jingyan_left">
							养宠经验
						</view>
						<view class="jingyan_right">
							30年以内
						</view>
					</view>
				</view>
				<view class="container">
					<view class="container_flex">
						<view class="progress-wrapper">
							<view class="progress-bar">
								<view class="progress-left" :style="{width: leftWidth3 + '%'}"></view>
								<view class="progress-right" :style="{width: rightWidth3 + '%'}"></view>
								<view class="thumb left" :style="{left: leftPosition3 + '%'}"></view>
								<view class="thumb right" :style="{left: rightPosition3 + '%'}"></view>
							</view>
						</view>
						<view class="progress-label">30年</view>
					</view>
					<view class="container_btn3">
						<view class="btn" :class="{ 'selected3': isSelected3(0,3) }" @click="chage3(0,3)">1-3年</view>
						<view class="btn" :class="{ 'selected3': isSelected3(3,5) }" @click="chage3(3,5)">3-5年</view>
						<view class="btn" :class="{ 'selected3': isSelected3(5,7) }" @click="chage3(5,7)">5-7年</view>
						<view class="btn" :class="{ 'selected3': isSelected3(7,10) }" @click="chage3(7,10)">7-10年</view>
						<view class="btn" :class="{ 'selected3': isSelected3(10,30) }" @click="chage3(10,30)">10年以上</view>
					</view>
				</view>
				<view class="qita">
					<view class="qita_top">
						<view class="qita_left">
							其他要求
						</view>
						<view class="qita_right">
							（多选）
						</view>
					</view>
				</view>
				<view class="duoxuan">
					<view class="checkbox" v-for="(item, index) in options" :key="index" @click="toggleCheckbox(index)">
						<view :class="{ 'checkbox-icon': true, 'checked': item.checked }">
						{{ item.name }}
						</view>
					</view>
				</view>
				<view class="boottom_confirm">
					<view class="reset" @click="reset">
						重置
					</view>
					<view class="_confirm" @click="confirmOpen">
						确定
					</view>
				</view>
				</scroll-view>
			</u-popup>
			<view>
				<!-- 普通弹窗 -->
				<uni-popup ref="popup" background-color="#fff" @change="change">
					<view class="popup-content" :class="{ 'popup-height': type === 'left' || type === 'right' }">
						<view class="fuwushiduan-top">
							<view class="fuwushiduan-top-text">
								服务时段
							</view>
							<view class="fuwushiduan-top-img" @click="guan">
								<image src="../../static/QQ截图20240401171515.png" mode=""></image>
							</view>
						</view>
						<view class="shiduan">
							<own-check :list="list1" color="#333" bgColor="#F2F2F2" activeTextColor="#666666"
								activeBgColor="#FFD1DB" type="2" :btnStyle="btnStyle" fontSize="22rpx"
								@chooseItem="chooseItems">
							</own-check>
						</view>
						<view class="shiduan">
							<own-check :list="list2" color="#333" bgColor="#F2F2F2" activeTextColor="#666666"
								activeBgColor="#FFD1DB" type="2" :btnStyle="btnStyle" fontSize="22rpx"
								@chooseItem="chooseItems">
							</own-check>
						</view>
						<view class="shiduan">
							<own-check :list="list3" color="#333" bgColor="#F2F2F2" activeTextColor="#666666"
								activeBgColor="#FFD1DB" type="2" :btnStyle="btnStyle2" fontSize="22rpx"
								@chooseItem="chooseItems">
							</own-check>
						</view>
						<view class="open" @click="querenThree">
							<text>确认</text>
						</view>
					</view>
				</uni-popup>
			</view>
			<view class="shaixuan" @click="show4 = true">
				筛选
				<image src="../../static/QQ截图20240403141954.png" mode=""></image>
			</view>
			<view class="didian">
				<view class="_img">
					<image src="../../static/地标-家@3x.png" mode=""></image>
				</view>
				<view class="dingwei">
					星巴克星巴克星巴克星巴克星巴克星巴克星巴克
				</view>
			</view>
			<u-popup :show="show2" @open="open">
				<view class="fuwu-baby-list">
					<view class="fuwu-baby-list-title">
						<view class="fuwu-baby-list-title-text">
							选择宝贝
						</view>
						<view class="fuwu-baby-list-title-icon" @click="guanbi">
							x
						</view>
					</view>
					<view class="fuwu-baby-list-top">
						服务宝贝&nbsp;&nbsp;(多选)
					</view>
					<view class="fuwu-baby-img">
						<view class="container">
							<!-- 选项卡 -->
							<view class="fuwu-baby-img">
								<view class="fuwu-baby-img-left">
									<view class="_img" :class="{ active: isTabActive('tab1') }"
										@click="changeTab('tab1')">
										<image v-if="isTabActive('tab1')" src="../../static/QQ截图20240331115853.png">
										</image>
										<image v-else src="../../static/QQ截图20240331120059.png"></image>
									</view>
								</view>
								<view class="fuwu-baby-img-right">
									<view class="_img" :class="{ active: isTabActive('tab2') }"
										@click="changeTab('tab2')">
										<image v-if="isTabActive('tab2')" src="../../static/QQ截图20240331115936.png">
										</image>
										<image v-else src="../../static/QQ截图20240331115754.png"></image>
									</view>
								</view>
							</view>
							<!-- 对应选项卡的内容 -->
							<view class="tab-content">
								<view v-if="isTabActive('tab2') ||isTabActive('tab1')">
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
							<view class="openbtn" @click="queren">
								确认
							</view>
						</view>
					</view>
				</view>
			</u-popup>
			<u-popup :show="tianjia" @close="close" @open="open">
				<view class="fuwu-baby-list">
					<view class="fuwu-baby-list-title">
						<view class="fuwu-baby-list-title-text">
							选择宝贝
						</view>
						<view class="fuwu-baby-list-title-icon" @click="guanbiTwo">
							x
						</view>
					</view>
					<view class="baobei-img">
						<view class="baobei-img_1">
							<view class="_img">
								<image src="../../static/logo.png" mode=""></image>
							</view>
							<view class="_text">
								哆啦哆啦哆啦
							</view>
						</view>
						<view class="baobei-img_2">
							<view class="_img">
								<image src="../../static/logo.png" mode=""></image>
							</view>
							<view class="_text">
								哆啦哆啦哆啦
							</view>
						</view>
						<view class="baobei-img_3">
							<view class="_img">
								<image src="../../static/logo.png" mode=""></image>
							</view>
							<view class="_text">
								哆啦哆啦哆啦
							</view>
						</view>
						<view class="baobei-img_4">
							<view class="_text1">
								+
							</view>
							<view class="_text2">
								新增宝贝
							</view>
						</view>
					</view>
					<view class="openbtn" @click="querenTwo">
						确认
					</view>
				</view>
			</u-popup>
		</view>
		<!-- <view class="kongtai">
			<view class="_image_">
				<image src="../../static/空态图-什么都没有@3x.png" mode=""></image>
				<view class="text">
					暂无可选宠托师哦~
				</view>
			</view>
			<view class="list">
				<view class="zuijin">
					<view class="zuijin-top">
						<view class="zuijin-top-text">
							离你最近
						</view>
						<view class="zuijin-top-img">
							<image src="../../static/标题尾巴@2x.png" mode=""></image>
						</view>
					</view>
				</view>
			</view>
			<view class="aa">
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
						<view class="chongtuoshi-list-left-text">
							清明3天可约
						</view>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text2">
							<image src="../../static/QQ截图20240402113837.png" mode=""></image>
							<text>五星宠托师</text>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
							<view class="img">
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
							</view>
							<view class="money">
								<text class="money_text1">￥</text>
								<text class="money_text2">40</text>
								<text class="money_text3">/次起</text>
							</view>
						</view>
					</view>
				</view>
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
						<view class="chongtuoshi-list-left-text">
							清明3天可约
						</view>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text2">
							<image src="../../static/QQ截图20240402113837.png" mode=""></image>
							<text>五星宠托师</text>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
							<view class="img">
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
							</view>
							<view class="money">
								<text class="money_text1">￥</text>
								<text class="money_text2">40</text>
								<text class="money_text3">/次起</text>
							</view>
						</view>
					</view>
				</view>
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
						<view class="chongtuoshi-list-left-text">
							清明3天可约
						</view>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text2">
							<image src="../../static/QQ截图20240402113837.png" mode=""></image>
							<text>五星宠托师</text>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
							<view class="img">
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
							</view>
							<view class="money">
								<text class="money_text1">￥</text>
								<text class="money_text2">40</text>
								<text class="money_text3">/次起</text>
							</view>
						</view>
					</view>
				</view>
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
						<view class="chongtuoshi-list-left-text">
							清明3天可约
						</view>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text2">
							<image src="../../static/QQ截图20240402113837.png" mode=""></image>
							<text>五星宠托师</text>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
							<view class="img">
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
								<image src="../../static/评分@3x.png" mode=""></image>
							</view>
							<view class="money">
								<text class="money_text1">￥</text>
								<text class="money_text2">40</text>
								<text class="money_text3">/次起</text>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view> -->

		<view class="content">
			<view class="chongtuoshi-list" @click="goxiangqing">
				<view class="chongtuoshi-list-left">
					<image src="../../static/logo.png" mode=""></image>
					<view class="chongtuoshi-list-left-text">
						清明3天可约
					</view>
				</view>
				<view class="chongtuoshi-list-right">
					<view class="text1">
						<view class="text1-left">
							泡泡泡泡泡泡
						</view>
						<view class="text1-left-img">
							<image src="../../static/女生@2x.png" mode=""></image>
						</view>
						<view class="text1-left-right">
							<text class="text_1">距您</text>
							<text class="text_2">0.8</text>
							<text class="text_3">km</text>
						</view>
					</view>
					<view class="text2">
						<image src="../../static/QQ截图20240402113837.png" mode=""></image>
						<text>五星宠托师</text>
					</view>
					<view class="text3">
						<text class="text3_1">养猫10年</text>
						<text class="text3_2">|</text>
						<text class="text3_3">服务过200次</text>
					</view>
					<view class="text4">
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
			<view class="chongtuoshi-list" @click="goxiangqing">
				<view class="chongtuoshi-list-left">
					<image src="../../static/logo.png" mode=""></image>
					<view class="chongtuoshi-list-left-text">
						清明3天可约
					</view>
				</view>
				<view class="chongtuoshi-list-right">
					<view class="text1">
						<view class="text1-left">
							泡泡泡泡泡泡
						</view>
						<view class="text1-left-img">
							<image src="../../static/女生@2x.png" mode=""></image>
						</view>
						<view class="text1-left-right">
							<text class="text_1">距您</text>
							<text class="text_2">0.8</text>
							<text class="text_3">km</text>
						</view>
					</view>
					<view class="text2">
						<image src="../../static/QQ截图20240402113837.png" mode=""></image>
						<text>五星宠托师</text>
					</view>
					<view class="text3">
						<text class="text3_1">养猫10年</text>
						<text class="text3_2">|</text>
						<text class="text3_3">服务过200次</text>
					</view>
					<view class="text4">
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
			<view class="chongtuoshi-list" @click="goxiangqing">
				<view class="chongtuoshi-list-left">
					<image src="../../static/logo.png" mode=""></image>
					<view class="chongtuoshi-list-left-text">
						清明3天可约
					</view>
				</view>
				<view class="chongtuoshi-list-right">
					<view class="text1">
						<view class="text1-left">
							泡泡泡泡泡泡
						</view>
						<view class="text1-left-img">
							<image src="../../static/女生@2x.png" mode=""></image>
						</view>
						<view class="text1-left-right">
							<text class="text_1">距您</text>
							<text class="text_2">0.8</text>
							<text class="text_3">km</text>
						</view>
					</view>
					<view class="text2">
						<image src="../../static/QQ截图20240402113837.png" mode=""></image>
						<text>五星宠托师</text>
					</view>
					<view class="text3">
						<text class="text3_1">养猫10年</text>
						<text class="text3_2">|</text>
						<text class="text3_3">服务过200次</text>
					</view>
					<view class="text4">
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
			<view class="chongtuoshi-list-bottom" @click="goxiangqing">
				<view class="chongtuoshi-list">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
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
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
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
				<view class="chongtuoshi-list" @click="goxiangqing">
					<view class="chongtuoshi-list-left">
						<image src="../../static/logo.png" mode=""></image>
					</view>
					<view class="chongtuoshi-list-right">
						<view class="text1">
							<view class="text1-left">
								泡泡泡泡泡泡
							</view>
							<view class="text1-left-img">
								<image src="../../static/女生@2x.png" mode=""></image>
							</view>
							<view class="text1-left-right">
								<text class="text_1">距您</text>
								<text class="text_2">0.8</text>
								<text class="text_3">km</text>
							</view>
						</view>
						<view class="text3">
							<text class="text3_1">养猫10年</text>
							<text class="text3_2">|</text>
							<text class="text3_3">服务过200次</text>
						</view>
						<view class="text4">
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

</template>

<script>
	import ownCheck from '@/components/own-checkBtn/own-check.vue';
	// #ifdef APP-PLUS
	const dom = weex.requireModule('dom');
	// #endif
	export default {
		components: {
			ownCheck
		},
		data() {
			return {
				options: [{
						name: '不限',
						checked: false
					},
					{
						name: '全天在家',
						checked: false
					},
					{
						name: '宠物可上床',
						checked: false
					},
					{
						name: '宠物可上沙发',
						checked: false
					},
					{
						name: '没有异宠',
						checked: false
					},
					{
						name: '未绝育可接',
						checked: false
					},
					{
						name: '发情期可接',
						checked: false
					},
					{
						name: '家中无狗',
						checked: false
					},
					{
						name: '家中无猫',
						checked: false
					},
				],
				selectedDistance:[0,0],// 初始状态为未选中
				selectedDistance2:[0,0],// 初始状态为未选中
				selectedDistance3:[0,0],// 初始状态为未选中
				leftPosition: 0,
				rightPosition: 100,
				leftWidth: 0,
				rightWidth: 100,
				leftPosition2: 0,
				rightPosition2: 100,
				leftWidth2: 0,
				rightWidth2: 100,
				leftPosition3: 0,
				rightPosition3: 100,
				leftWidth3: 0,
				rightWidth3: 100,
				startX: 0,
				barWidth: 520, // 进度条宽度，根据需要调整
				show: false,
				show2: false,
				show3: false,
				show4: false,
				tianjia: false,
				// isDisabled:true,
				mode: 'multiple',
				currentTabText: '',
				currentTabText2:'',
				defaultDateMultiple: [],
				selectedTabs: [],// 用于存储选中的选项
				currentTab: '',
				currentImg: '',
				columns: [
					['综合优先', '评分优先', '距离优先']
				],
				btnStyle: {
					"height": "96rpx",
					"line-height": "96rpx",
					"width": "312rpx",
					"border-radius": "11rpx",
					"font-size": '24rpx',
					"font-weight": "600",
				},
				btnStyle2: {
					"height": "96rpx",
					"line-height": "96rpx",
					"width": "654rpx",
					"font-size": '24rpx',
					"font-weight": "600",
					"border-radius": "11rpx",
				},
				list1: [{
						name: "6:00 ~ 11:00",
						type: 1,
					},
					{
						name: "11:00 ~ 14:00",
						type: 2,
					}
				],
				list2: [{
						name: "14:00 ~ 18:00",
						type: 3,
						isCheck: true
					},
					{
						name: "18:00 ~ 20:00",
						type: 4,
						isCheck: true
					}
				],
				list3: [{
					name: "全天",
					type: 5,
					isCheck: true
				}, ],
			}
		},
		methods: {
			 isTabActive(tabName) {
			      return this.selectedTabs.includes(tabName);
			    },
			confirmOpen(){
				this.show4=false
				// console.log(111);
			},
			reset(){
				this.currentTabText=''
				this.currentTabText2=''
				this.selectedDistance=[0,0]
				this.selectedDistance2 = [0, 0];
				this.selectedDistance3 = [0,0];
				this.leftWidth = 0
				this.rightWidth = 100
				this.leftPosition = 0
				this.rightPosition = 100
				this.leftWidth2 = 0
				this.rightWidth2 = 100
				this.leftPosition2 = 0
				this.rightPosition2 = 100
				this.leftWidth3 = 0
				this.rightWidth3 = 100
				this.leftPosition3 = 0
				this.rightPosition3 = 100
				this.options.forEach(option => {
				        option.checked = false;
				      });
			},
			toggleCheckbox(index) {
			  this.options[index].checked = !this.options[index].checked;
			},
			chage(min, max) {
				// 假设进度条最大值为10km，计算左右滑块的位置和宽度
				this.leftWidth = (min / 30) * 100;
				this.rightWidth = 100 - (max / 30) * 100;
				this.leftPosition = (min / 30) * 100;
				this.rightPosition = (max / 30) * 100;
				 if (this.selectedDistance[0] === min && this.selectedDistance[1] === max) {
				        // 如果当前选中的年限范围等于点击的年限范围，变颜色
				        this.selectedDistance = [0, 0];
				      } else {
				        // 否则，设置为点击的年限范围
				        this.selectedDistance = [min, max];
				      }
				 console.log(this.selectedDistance);
			},
			isSelected(min, max) {
			  // 判断当前按钮是否被选中
			  return this.selectedDistance[0] === min && this.selectedDistance[1] === max;
			},
			
			chage2(min, max) {
				// 假设进度条最大值为10km，计算左右滑块的位置和宽度
				this.leftWidth2 = (min / 150) * 100;
				this.rightWidth2 = 100 - (max / 150) * 100;
				this.leftPosition2 = (min / 150) * 100;
				this.rightPosition2 = (max / 150) * 100;
				if (this.selectedDistance2[0] === min && this.selectedDistance2[1] === max) {
				       // 如果当前选中的年限范围等于点击的年限范围，变颜色
				       this.selectedDistance2 = [0, 0];
				     } else {
				       // 否则，设置为点击的年限范围
				       this.selectedDistance2 = [min, max];
				     }
			},
			isSelected2(min, max) {
			  // 判断当前按钮是否被选中
			   return this.selectedDistance2[0] === min && this.selectedDistance2[1] === max;
			},
			chage3(min, max) {
				// 假设进度条最大值为10km，计算左右滑块的位置和宽度
				this.leftWidth3 = (min / 30) * 100;
				this.rightWidth3 = 100 - (max / 30) * 100;
				this.leftPosition3 = (min / 30) * 100;
				this.rightPosition3 = (max / 30) * 100;
				if (this.selectedDistance3[0] === min && this.selectedDistance3[1] === max) {
				       // 如果当前选中的年限范围等于点击的年限范围，变颜色
				       this.selectedDistance3 = [0, 0];
				     } else {
				       // 否则，设置为点击的年限范围
				       this.selectedDistance3 = [min, max];
				     }
			},
			isSelected3(min, max) {
			  // 判断当前按钮是否被选中
			   return this.selectedDistance3[0] === min && this.selectedDistance3[1] === max;
			},
			changeTabText(tab) {
				this.currentTabText = tab;
				// this.isDisabled = false
			},
			changeTabText2(tab) {
				this.currentTabText2 = tab;
				// this.isDisabled = false
			},
			chooseItems(e) {
				console.log(e)
			},
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
				this.show = false
			},
			toggle(type) {
				this.type = type
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.popup.open(type)
			},
			guan() {
				this.$refs.popup.close();
			},
			goxiangqing() {
				uni.navigateTo({
					url: '/pages/chongtuoshixiangqing/index'
				})
			},
			confirm() {
				console.log(111);
				this.show = false
			},
			conshijian(selectedDates) {
				this.defaultDateMultiple = selectedDates;
				console.log('日历选择：', selectedDates);
				this.show3 = false
				this.toggle('bottom');

				// this.isColor = true;
			},
			closes() {
				this.show3 = false
			},
			cancel() {
				this.show = false
			},
			toggle(type) {
				this.type = type
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.popup.open(type)
			},
			open() {
				// console.log('open');
			},
			close() {
				this.show = false
				// console.log('close');
			},
			changeTab(tabName) {
				if (this.selectedTabs.includes(tabName)) {
				        // 如果已经选中，则取消选中
				        this.selectedTabs = this.selectedTabs.filter(tab => tab !== tabName);
				      } else {
				        // 如果未选中，则添加到选中列表
				        this.selectedTabs.push(tabName);
				      }
				console.log(tabName,111);
				// this.isDisabled = false
			},
			changeImg(img) {
				this.currentImg = img
				console.log(img);
			},
			guanbi() {
				this.show2 = false
			},
			guanbiTwo() {
				this.tianjia = false
			},
			queren() {
				this.show2 = false
				this.tianjia = true
			},
			querenTwo() {
				this.tianjia = false
			},
			querenThree() {
				this.$refs.popup.close();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.box {
		background-color: #FFFFFF;
	}
	.color-scroll {
	  height: 1350rpx; /* 设置滚动区域的高度 */
	}
	.selected1 {
	  background-color: #FFD1DB !important; /* 选中状态的背景颜色 */
	}
	.selected2 {
	  background-color: #FFD1DB !important; /* 选中状态的背景颜色 */
	}
	.selected3 {
	  background-color: #FFD1DB !important; /* 选中状态的背景颜色 */
	}
	.boottom_confirm{
		position: fixed;
		bottom: 0;
		left: 0;
		display: flex;
		width: 750rpx;
		height: 154rpx;
		// margin-top: 30rpx;
		padding-top: 100rpx;
		background: linear-gradient( 180deg, rgba(255,255,255,0.25) 0%, #FFFFFF 10%);
		._confirm{
			width: 490rpx;
			height: 90rpx;
			background: #FFF133;
			border-radius: 102rpx;
			line-height: 90rpx;
			text-align: center;
		}
		.reset{
			margin-left: 40rpx;
			margin-right: 20rpx;
			width: 160rpx;
			height: 90rpx;
			background: #FFFFFF;
			border-radius: 102rpx;
			border: 4rpx solid #F6F8FA;
			line-height: 90rpx;
			text-align: center;
		}
	}
	.duoxuan {
		display: flex;
		flex-wrap: wrap;
		margin-left: 40rpx;
		padding-bottom: 250rpx;
	}

	.checkbox {
		display: flex;
		margin-bottom: 10px;
	}

	.checkbox-icon {
		// height: 20px;
		padding: 14rpx 45rpx;
		background-color: #F2F2F2;
		color: #666666;
		border-radius: 50rpx;
		margin-right: 10px;
		font-size: 24rpx;
	}

	.checked {
		background-color: #FFD1DB;
		color: #000;
		font-weight: 600;
	}

	.example-body {
		overflow: hidden;
	}

	.active {
		background-color: #FFD1DB !important;
	}

	.container {
		justify-content: center;
		align-items: center;
		margin-top: 40rpx;
	}

	.container_flex {
		display: flex;

		.progress-label {
			width: 54rpx;
			height: 28rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 500;
			font-size: 20rpx;
			color: rgba(0, 0, 0, 0.8);
			line-height: 28rpx;
			text-align: left;
			font-style: normal;
			margin-left: 50rpx;
		}
	}

	.container_btn3 {
		display: flex;
		padding-top: 40rpx;
		margin-left: 40rpx;
		flex-wrap: wrap;

		.btn {
			height: 36rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 24rpx;
			color: #666666;
			line-height: 36rpx;
			text-align: center;
			font-style: normal;
			text-transform: none;
			padding: 14rpx 40rpx;
			border-radius: 30rpx;
			margin-right: 30rpx;
			background-color: #F2F2F2;
			margin-bottom: 28rpx;
		}
	}

	.container_btn2 {
		display: flex;
		padding-top: 40rpx;
		margin-left: 40rpx;
		flex-wrap: wrap;

		.btn {
			height: 36rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 24rpx;
			color: #666666;
			line-height: 36rpx;
			text-align: center;
			font-style: normal;
			text-transform: none;
			padding: 14rpx 40rpx;
			border-radius: 30rpx;
			margin-right: 30rpx;
			background-color: #F2F2F2;
			margin-bottom: 28rpx;
		}
	}

	.container_btn {
		display: flex;
		padding-top: 40rpx;
		margin-left: 40rpx;

		.btn {
			height: 36rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 24rpx;
			color: #666666;
			line-height: 36rpx;
			text-align: center;
			font-style: normal;
			text-transform: none;
			padding: 14rpx 40rpx;
			border-radius: 30rpx;
			margin-right: 20rpx;
			background-color: #F2F2F2;
		}
	}

	.progress-wrapper {
		// display: flex;
		width: 520rpx;
		/* 进度条容器宽度，根据需要调整 */
		padding-left: 60rpx;
		margin-top: 10rpx;
	}

	.progress-bar {
		position: relative;
		height: 3px;
		/* 进度条高度，根据需要调整 */
		background-color: #FF5C7F;
	}

	.progress-left {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		background-color: #F2F2F2;
		/* 进度条左侧颜色，根据需要调整 */
	}

	.progress-right {
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;
		background-color: #F2F2F2;
		/* 进度条右侧颜色，根据需要调整 */
	}

	.thumb {
		position: absolute;
		top: 0;
		width: 20px;
		/* 拖动块宽度，根据需要调整 */
		height: 20px;
		background-image: url("../../static/进度条@3x.png");
		background-size: 100%;
		border-radius: 50%;
		transform: translate(-50%, -50%);
		touch-action: none;
	}

	.thumb.left {
		left: 0;
	}

	.thumb.right {
		right: 0;
	}

	.qita {
		.qita_top {
			display: flex;
			margin-top: 40rpx;
			margin-bottom: 40rpx;

			.qita_left {
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: left;
				font-style: normal;
				margin-left: 40rpx;
			}

			.qita_right {
				width: 112rpx;
				height: 34rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(0, 0, 0, 0.8);
				line-height: 34rpx;
				text-align: left;
				font-style: normal;
				margin-left: 16rpx;
				margin-top: 8rpx;
			}
		}
	}

	.jingyan {
		.jingyan_top {
			display: flex;
			margin-top: 40rpx;

			.jingyan_left {
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: left;
				font-style: normal;
				margin-left: 40rpx;
			}

			.jingyan_right {
				width: 112rpx;
				height: 34rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(0, 0, 0, 0.8);
				line-height: 34rpx;
				text-align: left;
				font-style: normal;
				margin-left: 16rpx;
				margin-top: 8rpx;
			}
		}
	}

	.jiage {
		.jiage_top {
			display: flex;
			margin-top: 40rpx;

			.jiage_left {
				width: 64rpx;
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: left;
				font-style: normal;
				margin-left: 40rpx;
			}

			.jiage_right {
				width: 112rpx;
				height: 34rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(0, 0, 0, 0.8);
				line-height: 34rpx;
				text-align: left;
				font-style: normal;
				margin-left: 16rpx;
				margin-top: 8rpx;
			}
		}
	}

	.juli {
		.juli_top {
			display: flex;
			margin-top: 40rpx;

			.juli_left {
				width: 64rpx;
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: left;
				font-style: normal;
				margin-left: 40rpx;
			}

			.juli_right {
				width: 112rpx;
				height: 34rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 24rpx;
				color: rgba(0, 0, 0, 0.8);
				line-height: 34rpx;
				text-align: left;
				font-style: normal;
				margin-left: 16rpx;
				margin-top: 8rpx;
			}
		}

	}

	.fuwu_pingfen {
		width: 64rpx;
		height: 44rpx;
		font-family: PingFangSC, PingFang SC;
		font-weight: 600;
		font-size: 32rpx;
		color: #000000;
		line-height: 44rpx;
		text-align: left;
		font-style: normal;
		margin-left: 40rpx;
		margin-bottom: 28rpx;
		margin-top: 40rpx;
	}

	.fuwu_xiangmu {
		width: 128rpx;
		height: 44rpx;
		font-family: PingFangSC, PingFang SC;
		font-weight: 600;
		font-size: 32rpx;
		color: #000000;
		line-height: 44rpx;
		text-align: right;
		font-style: normal;
		margin-left: 40rpx;
		margin-top: 84rpx;
		margin-bottom: 28rpx;
	}

	.list-radio {
		margin-top: 16rpx;

		.radio-text {
			display: flex;
			padding-left: 40rpx;

			.radio-text-left {
				margin-right: 20rpx;
				height: 64rpx;
				background: #F2F2F2;
				border-radius: 32rpx 32rpx 32rpx 32rpx;

				.text {
					height: 64rpx;
					border-radius: 32rpx 32rpx 32rpx 32rpx;

					text {
						height: 64rpx;
						font-family: PingFang SC, PingFang SC;
						font-weight: 600;
						font-size: 24rpx;
						color: #666666;
						line-height: 64rpx;
						font-style: normal;
						text-transform: none;
						margin: 14rpx 40rpx;
					}
				}
			}

			.radio-text-right {
				margin-right: 20rpx;
				height: 64rpx;
				margin-left: 4rpx;
				background: #F2F2F2;
				border-radius: 32rpx 32rpx 32rpx 32rpx;

				.text {
					// width: 128rpx;
					height: 64rpx;
					border-radius: 32rpx 32rpx 32rpx 32rpx;

					text {
						// width: 48rpx;
						height: 36rpx;
						font-family: PingFang SC, PingFang SC;
						font-weight: 600;
						font-size: 24rpx;
						color: #666666;
						line-height: 64rpx;
						text-align: center;
						font-style: normal;
						text-transform: none;
						margin: 14rpx 40rpx;
						padding-top: 8rpx;
					}
				}
			}
		}
	}

	.shiduan {
		display: flex;
		padding: 0 33rpx;
		justify-content: space-around;
		padding-top: 20rpx;
	}

	.fuwushiduan-top {
		display: flex;
		justify-content: space-between;

		.fuwushiduan-top-text {
			width: 128rpx;
			height: 44rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 600;
			font-size: 32rpx;
			color: #332828;
			line-height: 38rpx;
			text-align: center;
			font-style: normal;
			text-transform: none;
			margin-left: 312rpx;
			margin-top: 48rpx;
		}

		.fuwushiduan-top-img {
			width: 25rpx;
			height: 25rpx;
			border-radius: 0rpx 0rpx 0rpx 0rpx;
			margin-right: 48rpx;
			margin-top: 40rpx;

			image {
				width: 25rpx;
				height: 25rpx;
				border-radius: 0rpx 0rpx 0rpx 0rpx;
			}
		}
	}

	.open {
		width: 750rpx;
		height: 120rpx;
		line-height: 120rpx;
		text-align: center;
		border-top: 2rpx solid #EBE9E9;
		margin-top: 60rpx;

		text {
			width: 750rpx;
			height: 120rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 500;
			font-size: 32rpx;
			color: #D8D8D8;
			line-height: 38rpx;
			font-style: normal;
			text-transform: none;
		}
	}

	.tabs {
		background-color: #FFD1DB;
		display: flex;

		.paixu,
		.chongwu,
		.shijian,
		.shaixuan {
			width: 116rpx;
			height: 88rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 28rpx;
			color: #000000;
			line-height: 88rpx;
			text-align: center;
			position: relative;

			image {
				position: absolute;
				width: 12rpx;
				height: 12rpx;
				bottom: 20rpx;
			}
		}

		.paixu {
			padding-left: 40rpx;
		}
	}

	.didian {
		display: flex;
		width: 200rpx;
		height: 92rpx;

		.dingwei {
			width: 160rpx;
			height: 92rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 20rpx;
			color: #000000;
			line-height: 92rpx;
			text-align: left;
			font-style: normal;
			white-space: nowrap;
			/* 不换行 */
			overflow: hidden;
			/* 隐藏溢出部分 */
			text-overflow: ellipsis;
			/* 使用省略号 */
		}

		._img {
			line-height: 110rpx;

			image {
				width: 46rpx;
				height: 46rpx;
			}
		}
	}

	.fuwu-baby-list {
		.baobei-img {
			display: flex;
			margin-top: 30rpx;

			.baobei-img_1 {
				margin-left: 40rpx;
			}

			.baobei-img_4 {
				width: 144rpx;

				._text1 {
					width: 132rpx;
					height: 132rpx;
					border: 1px dashed #ADA9A9;
					border-radius: 100rpx;
					color: #ADA9A9;
					line-height: 110rpx;
					font-size: 80rpx;
				}

				._text2 {
					width: 144rpx;
					height: 34rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 400;
					font-size: 24rpx;
					color: rgba(0, 0, 0, 0.4);
					line-height: 34rpx;
					text-align: center;
					font-style: normal;
					margin-top: 24rpx;
				}
			}

			.baobei-img_1,
			.baobei-img_2,
			.baobei-img_3,
			.baobei-img_4 {
				width: 144rpx;
				text-align: center;
				margin-right: 32rpx;

				._img {
					width: 144rpx;
					height: 132rpx;

					image {
						width: 132rpx;
						height: 132rpx;
						border-radius: 100rpx;
					}
				}

				._text {
					font-family: PingFangSC, PingFang SC;
					font-weight: 600;
					font-size: 24rpx;
					color: #000000;
					line-height: 34rpx;
					text-align: center;
					font-style: normal;
					margin-top: 24rpx;
				}

			}
		}

		.fuwu-baby-list-title {
			width: 750rpx;
			height: 120rpx;
			display: flex;

			.fuwu-baby-list-title-text {
				width: 128rpx;
				height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 44rpx;
				text-align: right;
				font-style: normal;
				margin-left: 312rpx;
				margin-top: 38rpx;
			}

			.fuwu-baby-list-title-icon {
				width: 40rpx;
				height: 40rpx;
				font-size: 40rpx;
				margin-left: 238rpx;
				margin-top: 34rpx;
				color: #ADA9A9;
			}
		}

		.fuwu-baby-list-top {
			width: 224rpx;
			height: 40rpx;
			font-family: PingFang SC, PingFang SC;
			font-weight: 600;
			font-size: 28rpx;
			color: #ADA9A9;
			line-height: 33rpx;
			text-align: left;
			font-style: normal;
			text-transform: none;
			margin-left: 50rpx;
			margin-top: 24rpx;
		}

		.fuwu-baby-img {
			display: flex;
			margin-top: 16rpx;

			.fuwu-baby-img-left {
				margin-right: 16rpx;
				width: 144rpx;
				height: 144rpx;
				margin-left: 50rpx;
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

		.tab-content {
			.tixing {
				width: 112rpx;
				height: 40rpx;
				font-family: PingFang SC, PingFang SC;
				font-weight: 600;
				font-size: 28rpx;
				color: #ADA9A9;
				line-height: 33rpx;
				text-align: left;
				font-style: normal;
				text-transform: none;
				margin-left: 50rpx;
				margin-top: 40rpx;
				margin-bottom: 16rpx;
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

		}

		.openbtn {
			width: 750rpx;
			height: 154rpx;
			text-align: center;
			box-shadow: 2rpx 2rpx 0rpx 0rpx rgba(0, 0, 0, 0.05);
			color: #FF5C7F;
			line-height: 154rpx;
			font-weight: 600;
			border-top: 2rpx solid #ADA9A9;
			margin-top: 72rpx;
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
				width: 476rpx;
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
				margin-left: 16rpx;
			}

			.time-right {
				width: 24rpx;
				height: 24rpx;
				border-radius: 0rpx 0rpx 0rpx 0rpx;
				// margin-left: 182rpx;
				margin-top: 20rpx;

				image {
					width: 24rpx;
					height: 24rpx;
					border-radius: 0rpx 0rpx 0rpx 0rpx;
				}
			}
		}
	}

	.aa {
		background-color: #FFFFFF;
	}

	.kongtai {
		background-color: #FFD1DB;

		._image_ {
			padding-top: 80rpx;
			padding-left: 236rpx;
			position: relative;
			background-color: #FFD1DB;

			image {
				width: 280rpx;
				height: 280rpx;
			}

			.text {
				width: 280rpx;
				position: absolute;
				bottom: 10rpx;
				height: 40rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 28rpx;
				color: rgba(0, 0, 0, 0.6);
				line-height: 40rpx;
				text-align: center;
				font-style: normal;
			}
		}

		.zuijin {
			background-image: url('../../static/背景造型@2x.png');
			background-size: 100%;
			background-repeat: no-repeat;

			.zuijin-top {
				display: flex;
				position: relative;
				padding-bottom: 32rpx;

				.zuijin-top-text {
					width: 176rpx;
					height: 64rpx;
					font-family: AppleSystemUIFont;
					font-size: 44rpx;
					color: #000000;
					line-height: 64rpx;
					text-align: left;
					font-style: normal;
					margin-top: 80rpx;
					margin-left: 40rpx;
				}

				.zuijin-top-img {
					position: absolute;
					bottom: 34rpx;
					left: 200rpx;
					width: 48rpx;
					height: 30rpx;

					image {
						width: 48rpx;
						height: 30rpx;
					}
				}
			}
		}

		.chongtuoshi-list {
			margin-left: 40rpx;
			width: 660rpx;
			height: 256rpx;
			background: #FFFFFF;
			border-radius: 32rpx;
			border: 2rpx solid #000000;
			display: flex;
			box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
			margin-bottom: 34rpx;

			.chongtuoshi-list-left {
				width: 160rpx;
				height: 200rpx;
				background-image: url('../../static/宠托师背景@2x.png');
				background-size: 100%;
				background-repeat: no-repeat;
				border-radius: 28rpx;
				margin-left: 28rpx;
				margin-top: 28rpx;

				image {
					width: 160rpx;
					height: 164rpx;
					background: #CDC9C9;
					border-radius: 28rpx;
				}

				.chongtuoshi-list-left-text {
					width: 160rpx;
					height: 20rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 500;
					font-size: 20rpx;
					color: #FFFFFF;
					line-height: 20rpx;
					// text-align: left;
					text-align: center;
					font-style: normal;
					margin-bottom: 6rpx;
				}
			}

			.chongtuoshi-list-right {
				width: 420rpx;
				height: 188rpx;
				margin-top: 34rpx;
				margin-left: 24rpx;

				.text1 {
					display: flex;

					.text1-left {
						width: 168rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #111111;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
					}

					.text1-left-img {
						width: 32rpx;
						height: 32rpx;
						background: #FFD1DB;
						border-radius: 20rpx;
						margin-left: 12rpx;
						margin-top: 4rpx;

						image {
							width: 32rpx;
							height: 32rpx;
						}
					}

					.text1-left-right {
						.text_1 {
							width: 44rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 92rpx;
						}

						.text_2 {
							width: 34rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 4rpx;
							margin-right: 4rpx;
						}

						.text_3 {
							width: 32rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
						}
					}
				}

				.text2 {
					display: flex;

					image {
						margin-top: 6rpx;
						width: 30rpx;
						height: 30rpx;
					}

					text {
						width: 120rpx;
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #FF5C7F;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 12rpx;
						margin-top: 8rpx;
					}
				}

				.text3 {
					.text3_1 {
						width: 100rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 22rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
					}

					.text3_2 {
						font-size: 20rpx;
						color: #999999;
					}

					.text3_3 {
						width: 128rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 22rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
					}
				}

				.text4 {
					margin-top: 24rpx;
					display: flex;
					justify-content: space-between;

					.img {
						height: 32rpx;

						image {
							width: 32rpx;
							height: 32rpx;
							background: #FFD1DB;
							border-radius: 8rpx;
							margin-right: 4rpx;
						}
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

	.content {
		background-image: url('../../static/bg@3x.png');
		background-size: 100%;
		background-repeat: no-repeat;

		.chongtuoshi-list {
			margin-left: 40rpx;
			width: 660rpx;
			height: 256rpx;
			background: #FFFFFF;
			border-radius: 32rpx;
			border: 2rpx solid #000000;
			display: flex;
			box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
			margin-bottom: 34rpx;

			.chongtuoshi-list-left {
				width: 160rpx;
				height: 200rpx;
				background-image: url('../../static/宠托师背景@2x.png');
				background-size: 100%;
				background-repeat: no-repeat;
				border-radius: 28rpx;
				margin-left: 28rpx;
				margin-top: 28rpx;

				image {
					width: 160rpx;
					height: 164rpx;
					background: #CDC9C9;
					border-radius: 28rpx;
				}

				.chongtuoshi-list-left-text {
					width: 160rpx;
					height: 20rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 500;
					font-size: 20rpx;
					color: #FFFFFF;
					line-height: 20rpx;
					// text-align: left;
					text-align: center;
					font-style: normal;
					margin-bottom: 6rpx;
				}
			}

			.chongtuoshi-list-right {
				width: 420rpx;
				height: 188rpx;
				margin-top: 34rpx;
				margin-left: 24rpx;

				.text1 {
					display: flex;

					.text1-left {
						width: 168rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #111111;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
					}

					.text1-left-img {
						width: 32rpx;
						height: 32rpx;
						background: #FFD1DB;
						border-radius: 20rpx;
						margin-left: 12rpx;
						margin-top: 4rpx;

						image {
							width: 32rpx;
							height: 32rpx;
						}
					}

					.text1-left-right {
						.text_1 {
							width: 44rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 92rpx;
						}

						.text_2 {
							width: 34rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 4rpx;
							margin-right: 4rpx;
						}

						.text_3 {
							width: 32rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
						}
					}
				}

				.text2 {
					display: flex;

					image {
						margin-top: 6rpx;
						width: 30rpx;
						height: 30rpx;
					}

					text {
						width: 120rpx;
						height: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #FF5C7F;
						line-height: 24rpx;
						text-align: left;
						font-style: normal;
						margin-left: 12rpx;
						margin-top: 8rpx;
					}
				}

				.text3 {
					.text3_1 {
						width: 100rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 22rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
					}

					.text3_2 {
						font-size: 20rpx;
						color: #999999;
					}

					.text3_3 {
						width: 128rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 22rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
					}
				}

				.text4 {
					margin-top: 24rpx;
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

		.chongtuoshi-list-bottom {
			.chongtuoshi-list {
				margin-left: 40rpx;
				width: 660rpx;
				height: 256rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				display: flex;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				margin-bottom: 34rpx;

				.chongtuoshi-list-left {
					width: 160rpx;
					height: 200rpx;
					background-image: url('../../static/宠托师背景@2x.png');
					background-size: 100%;
					background-repeat: no-repeat;
					border-radius: 28rpx;
					margin-left: 28rpx;
					margin-top: 28rpx;

					image {
						width: 160rpx;
						height: 200rpx;
						background: #CDC9C9;
						border-radius: 28rpx;
					}
				}

				.chongtuoshi-list-right {
					width: 420rpx;
					height: 188rpx;
					margin-top: 46rpx;
					margin-left: 24rpx;

					.text1 {
						display: flex;

						.text1-left {
							width: 168rpx;
							height: 40rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 600;
							font-size: 28rpx;
							color: #111111;
							line-height: 40rpx;
							text-align: left;
							font-style: normal;
						}

						.text1-left-img {
							width: 32rpx;
							height: 32rpx;
							background: #FFD1DB;
							border-radius: 20rpx;
							margin-left: 12rpx;
							margin-top: 4rpx;

							image {
								width: 32rpx;
								height: 32rpx;
							}
						}

						.text1-left-right {
							.text_1 {
								width: 44rpx;
								height: 32rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 22rpx;
								color: #999999;
								line-height: 32rpx;
								text-align: center;
								font-style: normal;
								margin-left: 92rpx;
							}

							.text_2 {
								width: 34rpx;
								height: 32rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 22rpx;
								color: #999999;
								line-height: 32rpx;
								text-align: center;
								font-style: normal;
								margin-left: 4rpx;
								margin-right: 4rpx;
							}

							.text_3 {
								width: 32rpx;
								height: 32rpx;
								font-family: PingFangSC, PingFang SC;
								font-weight: 400;
								font-size: 22rpx;
								color: #999999;
								line-height: 32rpx;
								text-align: center;
								font-style: normal;
							}
						}
					}

					.text3 {
						margin-top: 8rpx;

						.text3_1 {
							width: 100rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: left;
							font-style: normal;
						}

						.text3_2 {
							font-size: 20rpx;
							color: #999999;
						}

						.text3_3 {
							width: 128rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 22rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: left;
							font-style: normal;
							margin-left: 16rpx;
						}
					}

					.text4 {
						margin-top: 36rpx;
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
</style>