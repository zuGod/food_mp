<template>
	<view>
		<view class="content">
			<image class="logo" src="/static/touxiang.jpg"></image>
			<view class="text-area">
				<text class="title">{{name}}</text>
			</view>
		</view>
		<view class="xian"></view>
		<navigator url="/pages/src/about/setting">
			<image class="icon" src="/static/icon/setup.png"></image>设置
		</navigator>
		<view class="xian"></view>
		<navigator url="/pages/src/about/about">
			<image class="icon" src="/static/icon/setup_account.png"></image>关于账户
		</navigator>
		<view class="xian"></view>
		<navigator url="/pages/src/about/can">
			<image class="icon" src="/static/icon/help.png"></image>帮助
		</navigator>
		<view class="xian"></view>
		<button class="button popup-info" @click="dialogToggle('info')">
			<text class="button-text info-text">退出</text>
		</button>
		<view>
			<!-- 提示信息弹窗 -->
			<uni-popup ref="message" type="message">
				<uni-popup-message :type="msgType" :message="messageText" :duration="2000"></uni-popup-message>
			</uni-popup>
		</view>
		
		<view>
			<!-- 提示窗示例 -->
			<uni-popup ref="alertDialog" type="dialog">
				<uni-popup-dialog :type="msgType" cancelText="关闭" confirmText="同意" title="通知" content="确定要退出登录吗" @confirm="dialogConfirm"
					@close="dialogClose"></uni-popup-dialog>
			</uni-popup>
		</view>
	</view>
</template>

<script>
	export default {

		data() {
			return {
				name: 'admin',
				type: 'center',
				msgType: 'success',
				messageText: '这是一条成功提示',
				value: ''
			}
		},
		onShow() {

		},
		onLoad() {

		},
		onPullDownRefresh() {
			console.log('页面下拉刷新了')
		},
		methods: {
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			toggle(type) {
				this.type = type
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.popup.open(type)
			},
			messageToggle(type) {
				this.msgType = type
				this.messageText = `这是一条${type}消息提示`
				this.$refs.message.open()
			},
			dialogToggle(type) {
				this.msgType = type
				this.$refs.alertDialog.open()
			},
			dialogConfirm() {
				console.log('点击确认')
				this.messageText = `点击确认了 ${this.msgType} 窗口`
				uni.navigateTo({
					url:'./index'
				})
				// this.$refs.message.open()
			},
			inputDialogToggle() {
				this.$refs.inputDialog.open()
			},
			dialogClose() {
				console.log('点击关闭')
			},
			dialogInputConfirm(val) {
				uni.showLoading({
					title: '3秒后会关闭'
				})

				setTimeout(() => {
					uni.hideLoading()
					console.log(val)
					this.value = val
					// 关闭窗口后，恢复默认内容
					this.$refs.inputDialog.close()
				}, 3000)
			},
			shareToggle() {
				this.$refs.share.open()
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		border-radius: 10rem;
		height: 200rpx;
		width: 200rpx;
		margin-top: 40rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 40rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: black;
	}

	.xian {
		height: 1rpx;
		width: 100%;
		background-color: gray;
		margin-top: 30rpx;
		margin-bottom: 30rpx;
	}

	.icon {
		width: 50rpx;
		height: 50rpx;
	}



	.button {
		margin-left: 20%;
		margin-right: 20%;
	}

	.popup-info {
		color: #fff;
		background-color: #00a2a2;
	}

	.info-text {
		color: #909399;
	}

	.button-text {
		color: #fff;
		font-size: 16px;
		text-align: center;
	}
</style>
