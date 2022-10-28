<template>
	<view>
		<form @submit="formSubmit" @reset="formReset">
			<view class="word">
				<view class="star">*</view>区域：
				<picker @change="bindPickerChange" :value="index" :range="array" class="picker">
					<view class="uni-input">{{ array[index] }}</view>
				</picker>
			</view>
			<view class="word">
				<view class="star">*</view>档口：
				<picker @change="bindPickerChangeTw" :value="index1" :range="array1" class="picker">
					<view class="uni-input">{{ array1[index1] }}</view>
				</picker>
			</view>
			<view class="word">
				<view class="star">*</view>批次：
				<picker @change="bindPickerChangeTh" :value="index2" :range="array2" class="picker">
					<view class="uni-input">{{ array2[index2] }}</view>
				</picker>
			</view>
			<view class="word">
				<view class="star">*</view>{{ shopName }}
				<input type="text" class="input6" @input="onInput1" v-model="shopName1" />
			</view>
			<view class="word">
				<view class="star">*</view>{{ shopNumber }}
				<input type="text" class="input2" @input="onInput2" v-model="shopNumber1" />
			</view>
			<view class="word">
				<view class="star">*</view>{{ shopLittleNumber }}
				<input type="text" class="input5" @input="onInput3" v-model="shopLittleNumber1" />
			</view>
			<view class="word">
				<view class="star">*</view>{{ checkNumber }}
				<input type="text" class="input4" @input="onInput4" v-model="checkNumber1" />
			</view>
			<view class="word">
				<view class="star">*</view>{{ user }}
				<input type="text" class="input3" @input="onInput5" v-model="user1" />
			</view>
			<view class="word">
				<view class="star">*</view>{{ timeShop }}
				<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChange" class="picker2">
					<view>{{ time }}</view>
				</picker>
			</view>
			<view class="word">
				<view class="star">*</view>{{ other }}
				<editor id="editor" :placeholder="placeholder" @ready="onEditorReady" class="editor" @editor="onEdit" v-model="Edite"/>
			</view>

			<button form-type="reset"  class="btn">重置</button>
			<button form-type="submit" class="btn">提交</button>
		</form>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				index: 0,
				index1: 0,
				index2: 0,
				array: [1, 2, 3, 4, 5, 6, 7],
				arrayy:['一','二','三','四','五','六','七'],
				array1: [1, 2, 3, 4, 5, 6, 7],
				arrayy1:['一','二','三','四','五','六','七'],
				array2: [1, 2, 3, 4, 5, 6, 7],
				arrayy2:['一','二','三','四','五','六','七'],
				shopName: "货品名称：",
				shopNumber: "进货数量（KG）：",
				shopLittleNumber: "样品数量（g）：",
				checkNumber: "检测标准值：",
				user: "收样员：",
				timeShop: "收样时间：",
				other: "备注：",
				time: "12:01",
				placeholder: "开始输入...",
				shopName1: "",
				shopNumber1: "",
				shopLittleNumber1: "",
				checkNumber1: "",
				user1: "",
				Edite:""
			};
		},
		methods: {
			onInput1(e) {
				this.shopName1 = e.target.value
			},
			onInput2(e) {
				this.shopNumber1 = e.target.value
			},

			onInput3(e) {
				this.shopLittleNumber1 = e.target.value
			},

			onInput4(e) {
				this.checkNumber1 = e.target.value
			},
			onInput5(e){
				this.user1 = e.target.value
			},
			onEdit(e){
				this.Edite=e.target.value
			},




			bindPickerChange: function(e) {
				console.log("picker发送选择改变，携带值为", e.detail.value);
				this.index = e.detail.value;
			},
			bindPickerChangeTw: function(e) {
				console.log("picker发送选择改变，携带值为", e.detail.value);
				this.index1 = e.detail.value;
			},
			bindPickerChangeTh: function(e) {
				console.log("picker发送选择改变，携带值为", e.detail.value);
				this.index2 = e.detail.value;
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();

				if (type === "start") {
					year = year - 60;
				} else if (type === "end") {
					year = year + 2;
				}
				month = month > 9 ? month : "0" + month;
				day = day > 9 ? day : "0" + day;
				return `${year}-${month}-${day}`;
			},
			bindPickerChange: function(e) {
				console.log("picker发送选择改变，携带值为", e.detail.value);
				this.index = e.detail.value;
			},
			bindTimeChange: function(e) {
				this.time = e.detail.value;
			},
			onEditorReady() {
				// #ifdef MP-BAIDU
				this.editorCtx =
					requireDynamicLib("editorLib").createEditorContext("editor");
				// #endif

				// #ifdef APP-PLUS || H5 ||MP-WEIXIN
				uni
					.createSelectorQuery()
					.select("#editor")
					.context((res) => {
						this.editorCtx = res.context;
					})
					.exec();
				// #endif
			},
			undo() {
				this.editorCtx.undo();
			},
			formSubmit: function(e) {
				const db = uniCloud.database();
				db.collection("goods").add({
					"region":"干货"+this.arrayy[this.index]+"区",
					"stall": this.arrayy1[this.index1],
					"batch_number": this.arrayy2[this.array2],
					"goods_name": this.goods_name1,
					"quantity_in": this.shopNumber1,
					"quantity_sample": this.shopLittleNumber1,
					"standard_value": this.checkNumber1,
					"receive_by": this.user1,
					"receive_time": this.time,
					"remarks": this.Edite
				})
				var formdata = e.detail.value;
				uni.showModal({
					content: "提交成功！",
					showCancel: false,
				});
			},
			formReset: function(e) {
				console.log("清空数据");
			},
		},
		computed: {
			startDate() {
				return this.getDate("start");
			},
			endDate() {
				return this.getDate("end");
			},
		},
	};
</script>
<style scoped>
	.star {
		color: red;
		float: left;
	}

	.word {
		font-size: 18px;
		font-style: initial;
		padding: 15px 20px;
	}

	.picker,
	input {
		border: 1px solid #333;
		width: 60%;
		float: right;
		margin-right: 60px;
	}

	.input2 {
		width: 50%;
		margin-right: 3px;
	}

	.input3 {
		margin-right: 40px;
	}

	.input4 {
		margin-right: 10px;
	}

	.input5 {
		width: 50%;
		margin-right: 10px;
	}

	.input6 {
		margin-right: 20px;
	}

	.picker2 {
		border: 1px solid #333;
		width: 60%;
		float: right;
		margin-right: 30px;
	}

	#editor {
		width: 90%;
		height: 100px;
		border: 1px solid rgb(90, 87, 87);
		margin-top: 10px;
	}
	.btn{
		float: left;
		width: 30%;
		margin: 0 30px;
		background-color: aqua;
	}
</style>
