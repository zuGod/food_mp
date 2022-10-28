<template>
	<view>
		<view>
			<button class="btn btn1" @click="navgateTo()">添加样品</button>
			<button class="btn">删除所选</button>
		</view>
		<view class="liebiao">
			<text class="title">抽检样品列表</text>
			<checkbox-group>
				<view v-for="(item,index) in yangpin" :key=index class="zuida">
					<view class="cida">
						<checkbox class="bianjie" />
					</view>
					<view class="dakuai">
						<view>
							<text class="fontstyle">{{item.region}}</text>
							<text class="fontstyle">{{item.stall}}</text>
						</view>
						<view>
							<text class="fontstyle">{{item.goods_name}}</text>
							<text class="fontstyle">{{item.receive_by}}</text>
						</view>
					</view>
					<view class="dakuai2">
						<text class="fontstyle2" @click="toggle('center')">详情</text>
						<navigator class="fontstyle2" url="./listShop">修改</navigator>
						<text class="fontstyle2" @click="toggle('center')">删除</text>
					</view>
				</view>
			</checkbox-group>
			<view>
				<!-- 普通弹窗 -->
				<uni-popup ref="popup" background-color="#fff" @change="change">
					<view class="popup-content tan" :class="{ 'popup-height': type === 'left' || type === 'right' }">
						<view>
							<text class="title2">—————— 样品数据详情 ——————</text>
							<text class="xiangxi">样品编号：</text>
							<text class="xiangxi">检测项目：</text>
							<text class="xiangxi">检测结果：</text>
							<text class="xiangxi">样品名称：</text>
							<text class="xiangxi">区域：</text>
							<text class="xiangxi">档口：</text>
							<text class="xiangxi">批次号：</text>
							<text class="xiangxi">进货数量(kg)：</text>
							<text class="xiangxi">样品数量(g)：</text>
							<text class="xiangxi">标准值：</text>
							<text class="xiangxi">初检数据：</text>
							<text class="xiangxi">复检数据：</text>
							<text class="xiangxi">收样员：</text>
							<text class="xiangxi">收样时间：</text>
						</view>
					</view>
				</uni-popup>
			</view>
			<view>
				<!-- 提示窗示例 -->
				<uni-popup ref="alertDialog" type="dialog">
					<uni-popup-dialog :type="msgType" cancelText="关闭" confirmText="同意" title="通知" content="确定要退出登录吗？"
						@confirm="dialogConfirm" @close="dialogClose">

					</uni-popup-dialog>
				</uni-popup>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// yangpin[{
				// 	check_task_id:Number,
				// 	check_by:'',
				// 	check_item_name:'',
				// 	check_appointment_detail_id:Number
				// }]
				yangpin:[
					
				],

				type: 'center',
				msgType: 'success',
				messageText: '这是一条成功提示',
				value: ''
			}
		},
		onLoad() {
			const db = uniCloud.database();
			db.collection("goods").get().then((res) => {
				// res 为数据库查询结果
				(res.result.data).forEach(item =>(this.yangpin).push(item));
				// console.log(res);
				console.log(this.yangpin)
			}).catch((e) => {
				console.log(e)
			});
		},
		methods: {
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			navgateTo() {
				console.log(12)
				uni.navigateTo({
					url: "./shop"
				})
			},
			toggle(type) {
				this.type = type
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.popup.open(type)
			},

		}
	}
</script>

<style>
	.btn {
		width: 30%;
		margin-left: 15%;
		margin-top: 10%;
		margin-bottom: 5%;
		font-size: 15px;
		float: left;
	}

	.btn1 {
		background-color: aqua;
	}

	.liebiao {
		clear: both;
	}

	.title {
		font-weight: bold;
	}

	.zuida {
		clear: both;
		display: flex;
		border: 1px solid black;
		width: 99%;
	}

	.cida {
		float: left;
		margin: 5px;
	}

	.dakuai {
		float: left;
	}

	.dakuai2 {
		float: right;
		display: flex;
	}

	.fontstyle {
		margin: 10px;
	}

	.fontstyle2 {
		margin-left: 10px;
		color: #39abab;
	}

	.tan {
		padding: 5px;
		border: 2px solid #39abab;
	}

	.title2 {
		font-weight: bold;
		font-size: 15px;
		color: #5d92ca;
		display: block;
	}

	.xiangxi {
		display: block;
		margin: 5px;
	}
</style>
