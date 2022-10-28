<template>
	<view>
		<text class="neirong">账号与安全</text>
		<view class="xian"></view>
		<text class="neirong">消息提示</text>
		<view class="xian"></view>
		<text class="neirong">勿扰模式</text>
		<view class="xian"></view>
		<text class="neirong">隐私</text>
		<view class="xian"></view>
		<text class="neirong">通用</text>
		<view class="xian"></view>
		<text class="neirong">关于系统</text>
		<view class="xian"></view>
		<text class="neirong">客服中心</text>
		<view class="xian"></view>
		<text class="neirong">检查版本更新</text>
		<view class="xian"></view>
		<button class="button popup-info" @click="dialogToggle('info')">
			<text class="button-text info-text">注销</text>
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
					url:'../index'
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
	.neirong{
		margin: 10px;
		font-size: 36rpx;
	}
	.xian{
		height: 1rpx;
		width: 100%;
		background-color: gray;
		margin-top: 30rpx;
		margin-bottom: 30rpx;
	}
	.zhuxiao{
		margin-left: 20%;
		margin-right: 20%;
		background-color: #00a2a2;
		color:white
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
