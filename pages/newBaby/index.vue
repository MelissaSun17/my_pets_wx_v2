<template>
	<view class="box">
		<view class="content">
			<view class="jibenziliao">
				<view class="jibenziliao-title">
					<view class="jibenziliao-title-left">
						基本资料
					</view>
					<view class="jibenziliao-title-right">
						初次见面，介绍一下宝贝吧~
					</view>
				</view>
				<view class="jibenziliao-name">
					<view class="jibenziliao-name-title">
						名字
					</view>
					<view class="jibenziliao-inp">
						<u-input fontSize='28rpx' placeholder="请输入宝贝名字" border="surround" v-model="value"
							@change="change" class="inp"></u-input>
					</view>
				</view>
				<view class="jibenziliao-kind">
					<view class="jibenziliao-kind-title">
						种类
					</view>
					<view class="jibenziliao-kind-zhonglei">
						<view class="btn" :class="{ active: selectedOption === 'option1' }"
							@click="selectOption('option1')">
							狗狗
						</view>
						<view class="btn" :class="{ active: selectedOption === 'option2' }"
							@click="selectOption('option2')">
							猫咪
						</view>
					</view>
					<view class="jibenziliao-kind-inp">
						<u-input fontSize='28rpx' placeholder="请输入宝贝品种（选填）" border="surround" v-model="value2"
							@change="change2" class="inp"></u-input>
					</view>
				</view>
				<view class="jibenziliao-jueyu">
					<view class="jibenziliao-jueyu-title">
						绝育
					</view>
					<view class="jibenziliao-jueyu-whether">
						<view class="btn" :class="{ active: selectedOption2 === 'option3' }"
							@click="selectOption2('option3')">
							是
						</view>
						<view class="btn" :class="{ active: selectedOption2 === 'option4' }"
							@click="selectOption2('option4')">
							否
						</view>
					</view>
				</view>
				<view class="jibenziliao-gender">
					<view class="jibenziliao-gender-title">
						性别
					</view>
					<view class="jibenziliao-gender-xingbie">
						<view class="btn" :class="{ active: selectedOption3 === 'option5' }"
							@click="selectOption3('option5')">
							妹妹
						</view>
						<view class="btn" :class="{ active: selectedOption3 === 'option6' }"
							@click="selectOption3('option6')">
							弟弟
						</view>
					</view>
				</view>
				<view class="jibenziliao-birthday">
					<view class="jibenziliao-birthday-title">
						<view class="jibenziliao-birthday-left">
							生日
						</view>
						<view class="jibenziliao-birthday-right">
							(选填)
						</view>
					</view>
					<view class="jibenziliao-birthday-riqi" @click="showShengRi = true">
						<view class="jibenziliao-birthday-riqi-left">
							请选择宝贝生日
						</view>
						<view class="jibenziliao-birthday-riqi-right">
							<image src="../../static/icon_arrow.png" mode=""></image>
						</view>
					</view>
					<u-datetime-picker :cancelText="cancelText" toolbar-class="custom-toolbar" title="请选择宠物生日"
						:show="showShengRi" v-model="value1" mode="date" @confirm='queDing' @cancel='quxiao'>
					</u-datetime-picker>
				</view>
			</view>

			<view class="chongwuziliao" v-if="selectedOption === 'option1'">
				<view class="chongwuziliao-title">
					<view class="chongwuziliao-title-left">
						狗狗资料
					</view>
					<view class="chongwuziliao-title-right">
						量狗定制的专属关怀~
					</view>
				</view>
				<view class="chongwuziliao-tixing">
					<view class="chongwuziliao-tixing-title">
						体型
					</view>
					<view class="chongwuziliao-tixing-daxiao">
						<view class="btn" :class="{ active: selectedOption4 === 'option7' }"
							@click="selectOption4('option7')">
							小型(＜10kg)
						</view>
						<view class="btn" :class="{ active: selectedOption4 === 'option8' }"
							@click="selectOption4('option8')">
							中型(10-35kg)
						</view>
						<view class="btn" :class="{ active: selectedOption4 === 'option9' }"
							@click="selectOption4('option9')">
							大型(＞35kg)
						</view>
					</view>
				</view>
				<view class="chongwuziliao-toilet">
					<view class="chongwuziliao-toilet-title">
						定点厕所
					</view>
					<view class="chongwuziliao-toilet-youwu">
						<view class="btn" :class="{ active: selectedOption5 === 'option10' }"
							@click="selectOption5('option10')">
							有
						</view>
						<view class="btn" :class="{ active: selectedOption5 === 'option11' }"
							@click="selectOption5('option11')">
							无
						</view>
					</view>
				</view>
				<view class="chongwuziliao-gouzheng">
					<view class="chongwuziliao-gouzheng-title">
						<view class="chongwuziliao-gouzheng-title-left">
							狗证
						</view>
						<view class="chongwuziliao-gouzheng-title-right">
							(选填)
						</view>
					</view>
					<view class="chongwuziliao-gouzheng-youwu">
						<view class="btn" :class="{ active: selectedOption6 === 'option12' }"
							@click="selectOption6('option12')">
							有
						</view>
						<view class="btn" :class="{ active: selectedOption6 === 'option13' }"
							@click="selectOption6('option13')">
							无
						</view>
					</view>
				</view>
				<view class="zhengming" v-if="selectedOption6 === 'option12'">
					<view class="">
						<u-upload :fileList="fileList1" @afterRead="afterRead" @delete="deletePic" name="1" multiple
							:maxCount="1" width="227" height="163">
							<image class="_img" src="../../static/QQ截图20240408154256.png" mode=""></image>
						</u-upload>
					</view>
				</view>
			</view>
			<view class="xinggeyuxiguan">
				<view class="xinggeyuxiguan-title">
					<view class="xinggeyuxiguan-title-left">
						性格与习惯
					</view>
					<view class="xinggeyuxiguan-title-right">
						帮助宠托师快速熟悉宝贝~
					</view>
				</view>
				<view class="baby-xingge">
					宝贝性格
				</view>
				<view class="baby-content">
					<view class="baby-content-neirong">
						<!-- 文本域 -->
						<textarea class="wenbenyu" placeholder="请输入宝贝性格描述" v-model="textareaContent"
							rows="10"></textarea>
					</view>
					<view class="kuaijiejian">
						<view class="biaoqian" v-for="(tag, index) in tags" :key="index" @click="toggleContent(tag)">
							{{ tag }}
						</view>
					</view>
				</view>
				<view class="chongwuziliao-chifan">
					<view class="chongwuziliao-chifan-title">
						吃饭频率
					</view>
					<view class="chongwuziliao-chifan-jici">
						<view class="btn" :class="{ active: selectedOption7 === 'option14' }"
							@click="selectOption7('option14')">
							1日1餐
						</view>
						<view class="btn" :class="{ active: selectedOption7 === 'option15' }"
							@click="selectOption7('option15')">
							1日2餐
						</view>
						<view class="btn" :class="{ active: selectedOption7 === 'option16' }"
							@click="selectOption7('option16')">
							1日3餐
						</view>
						<view class="btn" :class="{ active: selectedOption7 === 'option17' }"
							@click="selectOption7('option17')">
							自助
						</view>
					</view>
				</view>
			</view>
			<view class="baby-zhaopian">
				<view class="baby-zhaopian-title">
					<view class="baby-zhaopian-title-left">
						宝贝照片集
					</view>
					<view class="baby-zhaopian-title-right">
						炫耀一下宝贝的可爱瞬间~
					</view>
				</view>
				<view class="touxiang">
					<view class="">
						<u-upload :fileList="fileList2" @afterRead="afterRead2" @delete="deletePic2" name="2" multiple
							:maxCount="10" width="188" height="188">
							<image class="_img2" src="../../static/QQ截图20240408213821.png" mode=""></image>
						</u-upload>
						<image class="tupian" src="../../static/logo.png" mode="" @click="handleUploadClick = true">
						</image>
						<u-action-sheet @select="handleSelect" @close='close' round='30' :cancelText='guanbi'
							:actions="list" :title="title" :show="handleUploadClick"
							safeAreaInsetBottom="true"></u-action-sheet>
					</view>
				</view>
			</view>
			<view class="beizhu">
				<view class="beizhu-title">
					<view class="beizhu-title-left">
						备注
					</view>
					<view class="beizhu-title-right">
						（选填）还有什么要叮嘱的吗？
					</view>
				</view>
				<view class="beizhu-text">
					<textarea class="wenbenyu2" placeholder="请输入宝贝过敏史、药物治疗等注意事项" v-model="textareaContent2"
						rows="10"></textarea>
				</view>
			</view>
			<view class="kong">

			</view>
			<view class="dibuanniu">
				<image :src="isDisabled ? '../../static/确认添加-置灰@3x.png' : '../../static/确认添加-高亮@3x.png'" mode=""
					@click="handleClick">
				</image>
			</view>
			<u-overlay :show="overlay" @click="maskLayer">
				<view class="warp">
					<view class="rect" @tap.stop>
						<view class="rect-top">
							还差一点点就填完啦~
						</view>
						<view class="rect-bottom">
							<view class="rect-bottom-left" @click="leave">
								执意离开
							</view>
							<view class="rect-bottom-right" @click="goOn">
								继续填写
							</view>
						</view>
					</view>
				</view>
			</u-overlay>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

				title: '请选择',
				value: '',
				guanbi: '取消',
				value2: '',
				showShengRi: false,
				cancelText: 'X',
				value1: Number(new Date()),
				selectedOption: '', // 存储选中的选项
				selectedOption2: '', // 存储选中的选项
				selectedOption3: '', // 存储选中的选项
				selectedOption4: '', // 存储选中的选项
				selectedOption5: '', // 存储选中的选项
				selectedOption6: '', // 存储选中的选项
				selectedOption7: '', // 存储选中的选项
				fileList1: [],
				fileList2: [],
				tags: ['害怕陌生人', '胆子很小', '喜欢所有人', '对猫很友好', '对狗很友好', '社牛', '爱玩玩具', '爱叫的话唠'],
				textareaContent: '', // 存储文本域中的内容
				textareaContent2: '',
				isDisabled: true,
				handleUploadClick: false,
				canProceed: false,
				overlay: false,
				list: [{
						name: '设置头像',
					},
					{
						name: '从手机选择',
					},
					{
						name: '去拍摄', //开启后文字不显示
					}
				],
			}
		},
		methods: {
			maskLayer() {
				this.overlay = true
			},
			leave(){
				console.log('离开');
				this.overlay = false
			},
			goOn(){
				console.log('继续');
				this.overlay = false
			},
			handleClick() {
				if (!this.isDisabled) {
					if (this.value.trim() !== '' && this.value2.trim() !== '' &&
						this.selectedOption !== '' && this.selectedOption2 !== '' &&
						this.selectedOption3 !== '' && this.selectedOption4 !== '' &&
						this.selectedOption5 !== '' && this.selectedOption6 !== '' &&
						this.selectedOption7 !== '' && this.textareaContent !== '' &&
						this.textareaContent2 !== ''
					) {
						console.log(111);
					} else {
						this.maskLayer()
						//提示用户
					}

				}
			},
			close() {
				this.handleUploadClick = false
			},
			handleSelect(item) {
				console.log('选择了：', item);
				if (item.name === '设置头像') {
					console.log(111);
				} else if (item.name === '从手机选择') {
					console.log(222);
				} else if (item.name === '去拍摄') {
					console.log(333);
				}
			},
			queDing() {
				this.showShengRi = false
			},
			quxiao() {
				this.showShengRi = false
			},
			toggleContent(tag) {
				// 检查文本域中是否已经包含了该标签内容
				if (this.textareaContent.includes(tag)) {
					// 如果包含，则移除该标签内容
					this.textareaContent = this.textareaContent.replace(tag + '、', '').trim();
				} else {
					// 如果不包含，则添加该标签内容
					this.textareaContent += tag + '、';
				}
			},
			deletePic(event) {
				this[`fileList${event.name}`].splice(event.index, 1)
			},
			// 新增图片
			async afterRead(event) {
				// 当设置 multiple 为 true 时, file 为数组格式，否则为对象格式
				let lists = [].concat(event.file)
				let fileListLen = this[`fileList${event.name}`].length
				lists.map((item) => {
					this[`fileList${event.name}`].push({
						...item,
						status: 'uploading',
						message: '上传中'
					})
				})
				for (let i = 0; i < lists.length; i++) {
					const result = await this.uploadFilePromise(lists[i].url)
					let item = this[`fileList${event.name}`][fileListLen]
					this[`fileList${event.name}`].splice(fileListLen, 1, Object.assign(item, {
						status: 'success',
						message: '',
						url: result
					}))
					fileListLen++
				}
			},
			uploadFilePromise(url) {
				return new Promise((resolve, reject) => {
					let a = uni.uploadFile({
						url: 'http://192.168.2.21:7001/upload', // 仅为示例，非真实的接口地址
						filePath: url,
						name: 'file',
						formData: {
							user: 'test'
						},
						success: (res) => {
							setTimeout(() => {
								resolve(res.data.data)
							}, 1000)
						}
					});
				})
			},
			deletePic2(event) {
				this[`fileList${event.name}`].splice(event.index, 2)
			},
			// 新增图片
			async afterRead2(event) {
				// 当设置 multiple 为 true 时, file 为数组格式，否则为对象格式
				let lists = [].concat(event.file)
				let fileListLen = this[`fileList${event.name}`].length
				lists.map((item) => {
					this[`fileList${event.name}`].push({
						...item,
						status: 'uploading',
						message: '上传中'
					})
				})
				for (let i = 0; i < lists.length; i++) {
					const result = await this.uploadFilePromise(lists[i].url)
					let item = this[`fileList${event.name}`][fileListLen]
					this[`fileList${event.name}`].splice(fileListLen, 2, Object.assign(item, {
						status: 'success',
						message: '',
						url: result
					}))
					fileListLen++
				}
			},
			uploadFilePromise(url) {
				return new Promise((resolve, reject) => {
					let a = uni.uploadFile({
						url: 'http://192.168.2.21:7001/upload', // 仅为示例，非真实的接口地址
						filePath: url,
						name: 'file',
						formData: {
							user: 'test'
						},
						success: (res) => {
							setTimeout(() => {
								resolve(res.data.data)
							}, 1000)
						}
					});
				})
			},
			change(e) {
				console.log('change', e);
			},
			change2(e) {
				console.log('change', e);
			},
			selectOption(option) {
				if (this.selectedOption === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption = option;
					this.isDisabled = false
					console.log(option);
				}
			},
			selectOption2(option) {
				if (this.selectedOption2 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption2 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption2 = option;
					this.isDisabled = false
				}
			},
			selectOption3(option) {
				if (this.selectedOption3 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption3 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption3 = option;
					this.isDisabled = false
				}
			},
			selectOption4(option) {
				if (this.selectedOption4 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption4 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption4 = option;
					this.isDisabled = false
				}
			},
			selectOption5(option) {
				if (this.selectedOption5 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption5 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption5 = option;
					this.isDisabled = false
				}
			},
			selectOption6(option) {
				if (this.selectedOption6 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption6 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption6 = option;
					this.isDisabled = false
				}
			},
			selectOption7(option) {
				if (this.selectedOption7 === option) {
					// 如果当前选项已经被选中，则取消选中状态
					this.selectedOption7 = '';
					this.isDisabled = true
				} else {
					// 否则设置为选中状态
					this.selectedOption7 = option;
					this.isDisabled = false
				}
			},
		}
	}
</script>

<style lang="less" scoped>
	.kong {
		height: 200rpx;
	}

	/deep/.u-icon__icon.data-v-172979f2 {
		display: none;
	}

	.warp {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100%;
	}

	.rect {
		width: 600rpx;
		height: 260rpx;
		border-radius: 36rpx;
		background-color: #fff;
		.rect-top{
			width: 440rpx;
			height: 40rpx;
			font-family: PingFangSC, PingFang SC;
			font-weight: 400;
			font-size: 28rpx;
			color: #000000;
			line-height: 40rpx;
			text-align: center;
			font-style: normal;
			margin-left: 80rpx;
			margin-top: 70rpx;
		}
		.rect-bottom{
			display: flex;
			justify-content: space-around;
			background-color: #F6F8FA ;
			margin-top: 50rpx;
			border-radius:0 0 36rpx 36rpx;
			.rect-bottom-left{
				// width: 128rpx;
				// height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 400;
				font-size: 32rpx;
				color: #000000;
				line-height: 100rpx;
				text-align: center;
				font-style: normal;
			}
			.rect-bottom-right{
				// width: 128rpx;
				// height: 44rpx;
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 32rpx;
				color: #000000;
				line-height: 100rpx;
				text-align: center;
				font-style: normal;
			}
		}
	}

	.tupian {
		width: 188rpx;
		height: 188rpx;
	}

	.custom-toolbar {
		justify-content: flex-end;
	}

	u-datetime-picker {
		position: relative;
		height: 300rpx !important;
	}

	/deep/.u-action-sheet__header.data-v-6766c527 {
		padding-top: 32rpx;
		padding-bottom: 32rpx;
	}

	/deep/.u-action-sheet__cancel-text.data-v-6766c527 {
		margin-bottom: 30rpx;
	}

	/deep/.u-reset-button.data-v-6766c527 {
		background-color: #FFFFFF !important;
		color: #000;
		font-weight: 600;
	}

	/deep/.u-picker.data-v-d45639b2 {
		padding-top: 155rpx;
	}

	/deep/.u-toolbar__title.data-v-6d25fc6f {
		position: absolute;
		width: 224rpx;
		height: 44rpx;
		font-family: PingFangSC, PingFang SC;
		font-weight: 600;
		font-size: 32rpx;
		color: #000000;
		line-height: 44rpx;
		font-style: normal;
		margin-left: 204rpx;
		top: 0;
		margin-top: 38rpx;
	}

	/deep/.u-toolbar__wrapper__confirm.data-v-6d25fc6f {
		width: 750rpx;
		height: 100rpx;
		line-height: 100rpx;
		padding-left: 350rpx;
		font-weight: 600;
		color: #FF5C7F !important;
		border-top: 4rpx solid #C3C3C3;
	}

	/deep/.u-toolbar__wrapper__cancel.data-v-6d25fc6f {
		position: absolute;
		right: 0;
		top: 0;
		margin-top: 40rpx;
		margin-right: 47rpx;
	}

	.zhengming {
		margin-top: 24rpx;
		margin-left: 32rpx;
	}

	._img {
		width: 596rpx;
		height: 128rpx;
		margin-top: 16rpx;
	}

	._img2 {
		width: 188rpx;
		height: 188rpx;
		border-radius: 30rpx;
	}

	.box {
		height: 100vh;
		background-color: #FFFFFF;

		.content {
			height: 100vh;
			background-image: url('../../static/bg@4x.png');
			background-size: 100%;
			background-repeat: no-repeat;
			padding-top: 24rpx;

			.jibenziliao {
				width: 660rpx;
				height: 914rpx;
				margin-left: 40rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);

				.jibenziliao-title {
					display: flex;

					.jibenziliao-title-left {
						width: 112rpx;
						height: 40rpx;
						margin-top: 24rpx;
						margin-left: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #000000;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
					}

					.jibenziliao-title-right {
						width: 300rpx;
						height: 32rpx;
						margin-top: 28rpx;
						margin-left: 16rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
					}
				}

				.jibenziliao-name {
					.jibenziliao-name-title {
						width: 48rpx;
						height: 34rpx;
						margin-left: 32rpx;
						margin-top: 24rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
					}

					.jibenziliao-inp {
						margin-top: 16rpx;
						width: 596rpx;
						height: 76rpx;
						padding-top: 4rpx;
						line-height: 80rpx;
						margin-left: 32rpx;
						background: #F2F2F2;
						border-radius: 20rpx;
					}
				}

				.jibenziliao-kind {
					.jibenziliao-kind-title {
						width: 48rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.jibenziliao-kind-zhonglei {
						display: flex;
						margin-left: 32rpx;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							width: 128rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;
						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}

					.jibenziliao-kind-inp {
						margin-top: 16rpx;
						width: 596rpx;
						height: 76rpx;
						padding-top: 4rpx;
						line-height: 80rpx;
						margin-left: 32rpx;
						background: #F2F2F2;
						border-radius: 20rpx;
					}
				}

				.jibenziliao-jueyu {
					.jibenziliao-jueyu-title {
						width: 48rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.jibenziliao-jueyu-whether {
						display: flex;
						margin-left: 32rpx;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							width: 104rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;
						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}
				}

				.jibenziliao-gender {
					.jibenziliao-gender-title {
						width: 48rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.jibenziliao-gender-xingbie {
						display: flex;
						margin-left: 32rpx;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							width: 128rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;
						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}
				}

				.jibenziliao-birthday {
					.jibenziliao-birthday-title {
						display: flex;

						.jibenziliao-birthday-left {
							margin-top: 26rpx;
							margin-left: 32rpx;
							width: 48rpx;
							height: 34rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 24rpx;
							color: #000000;
							line-height: 34rpx;
							text-align: left;
							font-style: normal;
						}

						.jibenziliao-birthday-right {
							width: 96rpx;
							height: 32rpx;
							margin-top: 26rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 24rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 8rpx;
						}
					}
				}

				.jibenziliao-birthday-riqi {
					width: 596rpx;
					height: 80rpx;
					background: #F2F2F2;
					border-radius: 20rpx;
					margin-top: 16rpx;
					margin-left: 32rpx;
					line-height: 80rpx;
					display: flex;
					justify-content: space-between;

					.jibenziliao-birthday-riqi-left {
						// width: 196rpx;
						// height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 28rpx;
						color: #999999;
						line-height: 80rpx;
						text-align: left;
						font-style: normal;
						text-transform: none;
						margin-left: 24rpx;

					}

					.jibenziliao-birthday-riqi-right {
						width: 24rpx;
						height: 24rpx;
						margin-right: 24rpx;

						image {
							width: 24rpx;
							height: 24rpx;
						}
					}
				}
			}

			.chongwuziliao {
				margin-left: 40rpx;
				margin-top: 34rpx;
				width: 660rpx;
				// height: 778rpx;
				padding-bottom: 30rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);

				.chongwuziliao-title {
					display: flex;

					.chongwuziliao-title-left {
						width: 112rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #000000;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.chongwuziliao-title-right {
						width: 228rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
						margin-top: 28rpx;
					}
				}

				.chongwuziliao-tixing {
					.chongwuziliao-tixing-title {
						width: 48rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.chongwuziliao-tixing-daxiao {
						display: flex;
						margin-left: 32rpx;
						flex-wrap: wrap;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							padding: 0 40rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;
						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}
				}

				.chongwuziliao-toilet {
					.chongwuziliao-toilet-title {
						width: 96rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.chongwuziliao-toilet-youwu {
						display: flex;
						margin-left: 32rpx;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							width: 104rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;

						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}
				}

				.chongwuziliao-gouzheng {
					.chongwuziliao-gouzheng-title {
						display: flex;

						.chongwuziliao-gouzheng-title-left {
							width: 48rpx;
							height: 34rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 24rpx;
							color: #000000;
							line-height: 34rpx;
							text-align: left;
							font-style: normal;
							margin-left: 32rpx;
							margin-top: 24rpx;
						}

						.chongwuziliao-gouzheng-title-right {
							width: 96rpx;
							height: 32rpx;
							font-family: PingFangSC, PingFang SC;
							font-weight: 400;
							font-size: 24rpx;
							color: #999999;
							line-height: 32rpx;
							text-align: center;
							font-style: normal;
							margin-left: 8rpx;
							margin-top: 24rpx;
						}
					}

					.chongwuziliao-gouzheng-youwu {
						display: flex;
						margin-left: 32rpx;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							width: 104rpx;
							height: 64rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;

						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}
				}
			}

			.xinggeyuxiguan {
				width: 660rpx;
				height: 740rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				margin-top: 34rpx;
				margin-left: 40rpx;

				.xinggeyuxiguan-title {
					display: flex;

					.xinggeyuxiguan-title-left {
						width: 140rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #000000;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.xinggeyuxiguan-title-right {
						width: 276rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
						margin-top: 28rpx;
					}
				}

				.baby-xingge {
					width: 96rpx;
					height: 34rpx;
					font-family: PingFangSC, PingFang SC;
					font-weight: 400;
					font-size: 24rpx;
					color: #000000;
					line-height: 34rpx;
					text-align: left;
					font-style: normal;
					margin-top: 24rpx;
					margin-left: 32rpx;
					margin-bottom: 16rpx;
				}

				.baby-content {
					width: 596rpx;
					height: 352rpx;
					background: #F2F2F2;
					border-radius: 20rpx;
					margin-left: 32rpx;

					.baby-content-neirong {
						// background-color: #FFD1DB;
						// width: 548rpx;
						// height: 190rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 500;
						font-size: 24rpx;
						margin-left: 24rpx;
						padding-top: 30rpx;
						color: #333333;
						text-align: left;
						font-style: normal;
						text-transform: none;
						display: flex;
						flex-wrap: wrap;

						.wenbenyu {
							display: flex;
							white-space: nowrap;
							height: 160rpx;
						}
					}

					.kuaijiejian {
						display: flex;
						flex-wrap: wrap;
						margin-left: 26rpx;

						.biaoqian {
							width: 130rpx;
							height: 48rpx;
							font-size: 18rpx;
							color: #000000;
							background: #FFFFFF;
							border-radius: 66rpx;
							line-height: 48rpx;
							text-align: center;
							margin-right: 8rpx;
							margin-top: 22rpx;
						}
					}
				}

				.chongwuziliao-chifan {
					.chongwuziliao-chifan-title {
						width: 96rpx;
						height: 34rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #000000;
						line-height: 34rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.chongwuziliao-chifan-jici {
						display: flex;
						margin-left: 32rpx;
						flex-wrap: wrap;

						.btn {
							margin-top: 16rpx;
							margin-right: 20rpx;
							// width: 104rpx;
							height: 64rpx;
							padding: 0 40rpx;
							background: #F2F2F2;
							border-radius: 66rpx;
							text-align: center;
							font-size: 24rpx;
							color: #666666;
							line-height: 64rpx;

						}

						.active {
							background-color: #FFD1DB;
							/* 设定选中状态的背景色 */
							color: black;
							/* 设定选中状态的文字颜色 */
						}
					}

				}

			}

			.baby-zhaopian {
				width: 660rpx;
				padding-bottom: 32rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				margin-left: 40rpx;
				margin-top: 34rpx;

				.baby-zhaopian-title {
					display: flex;

					.baby-zhaopian-title-left {
						width: 140rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #000000;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.baby-zhaopian-title-right {
						width: 276rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
						margin-top: 28rpx;
					}
				}

				.touxiang {
					margin-left: 32rpx;
					margin-top: 40rpx;
				}
			}

			.beizhu {
				width: 660rpx;
				height: 420rpx;
				background: #FFFFFF;
				border-radius: 32rpx;
				border: 2rpx solid #000000;
				box-shadow: 10rpx 15rpx rgba(0, 0, 0, 2);
				margin-left: 40rpx;
				margin-top: 34rpx;

				.beizhu-title {
					display: flex;

					.beizhu-title-left {
						width: 56rpx;
						height: 40rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 600;
						font-size: 28rpx;
						color: #000000;
						line-height: 40rpx;
						text-align: left;
						font-style: normal;
						margin-left: 32rpx;
						margin-top: 24rpx;
					}

					.beizhu-title-right {
						width: 336rpx;
						height: 32rpx;
						font-family: PingFangSC, PingFang SC;
						font-weight: 400;
						font-size: 24rpx;
						color: #999999;
						line-height: 32rpx;
						text-align: left;
						font-style: normal;
						margin-left: 16rpx;
						margin-top: 28rpx;
					}
				}

				.beizhu-text {
					.wenbenyu2 {
						margin-top: 24rpx;
						margin-left: 32rpx;
						background: #F2F2F2;
						border-radius: 20rpx;
						padding-top: 32rpx;
						padding-left: 24rpx;
						// padding-right: 24rpx;
					}
				}
			}

			.dibuanniu {
				position: fixed;
				bottom: 0;
				left: 0;
				width: 750rpx;
				height: 154rpx;
				background: #FFFFFF;
				padding-bottom: 30rpx;

				image {
					width: 660rpx;
					height: 106rpx;
					margin-left: 40rpx;
					margin-top: 24rpx;
				}
			}
		}
	}
</style>