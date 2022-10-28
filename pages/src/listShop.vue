<template>
	<view>
		<form @submit="formSubmit" @reset="formReset" class="from">
			<view class="title">{{ title }}</view>

			<view class="word">
				<view class="star">*</view>{{ idai }}
				<input type="text" class="input6"  @input="onInput1" v-model="s1" />
			</view>

			<view class="word">
				<view class="star">*</view>检测项目：
				<input type="text" class="input6"  @input="onInput2" v-model="s2" />
			</view>
			<view class="word">
				<view class="star">*</view>检测结果：
				<input type="text" class="input6" @input="onInput3" v-model="s3"/>
			</view>

			<view class="word">
				<view class="star">*</view>{{ shopName }}
				<input type="text" class="input6" @input="onInput4" v-model="s4"/>
			</view>

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
				<view class="star">*</view>{{ number }}
				<picker @change="bindPickerChangeTh" :value="index2" :range="array2" class="picker3">
					<view class="uni-input">{{ array2[index2] }}</view>
				</picker>
			</view>


			<view class="word">
				<view class="star">*</view>{{ shopNumber }}
				<input type="text" class="input2" @input="onInput5" v-model="s5"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ shopLittleNumber }}
				<input type="text" class="input5" @input="onInput6" v-model="s6"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ checkNumber }}
				<input type="text" class="input4" @input="onInput7" v-model="s7"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ first }}
				<input type="text" class="input6" @input="onInput8" v-model="s8"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ again }}
				<input type="text" class="input6" @input="onInput9" v-model="s9"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ user }}
				<input type="text" class="input7" @input="onInput10" v-model="s10"/>
			</view>
			<view class="word">
				<view class="star">*</view>{{ timeShop }}
				<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChange" class="picker2">
					<view>{{ time }}</view>
				</picker>
			</view>
			<view class="word">
				<view class="star">*</view>{{ other }}
				<editor id="editor" :placeholder="placeholder" @ready="onEditorReady" class="editor" @editor="onEdit" v-model="Edite"></editor>
			</view>

			<button form-type="submit" class="tijiao">提交</button>
			<!-- <button form-type="reset">重置</button> -->
		</form>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				title: "编辑修改样品数据",
				index: 0,
				index1: 0,
				index2: 0,
				array: [1, 2, 3, 4, 5, 6, 7],
				arrayy:['一','二','三','四','五','六','七'],
				array1: [1, 2, 3, 4, 5, 6, 7],
				arrayy1:['一','二','三','四','五','六','七'],
				array2: [1, 2, 3, 4, 5, 6, 7],
				arrayy2:['一','二','三','四','五','六','七'],
				idai: "样品编号：",
				shopName: "样品名称：",
				arei: "区域：",
				number: "批次号：",
				shopNumber: "进货数量（KG）：",
				shopLittleNumber: "样品数量（g）：",
				checkNumber: "检测标准值：",
				user: "收样员：",
				timeShop: "收样时间：",
				other: "备注：",
				time: "12:01",
				placeholder: "开始输入...",
				mustNumber: "标准值：",
				first: "初检数据：",
				again: "复检数据：",
				s1:"",
				s2:"",
				s3:"",
				s4:"",
				s5:"",
				s6:"",
				s7:"",
				s8:"",
				s9:"",
				s10:"",
				Edite:"",
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
			onInput5(e) {
				this.user1 = e.target.value
			},
			onInput6(e) {
				this.user1 = e.target.value
			},
			onInput7(e) {
				this.user1 = e.target.value
			},
			onInput8(e) {
				this.user1 = e.target.value
			},
			onInput9(e) {
				this.user1 = e.target.value
			},
			onInput10(e) {
				this.user1 = e.target.value
			},
			onEdit(e) {
				this.Edite = e.target.value
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
					"sample_code":s1,
					"check_item": s2,
					"check_result": s3,
					"sample_name": s4,
					"region":this.arrayy[this.index],
					"stall": this.arrayy1[this.array1],
					"batch_number": this.arrayy2[this.array2],
					"quantity_in": s5,
					"quantity_sample": s6,
					"standard_value": s7,
					"check_data":s8,
					"recheck_data": s9,
					"receive_by": s10,
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
		padding: 12px 20px;
		margin-left: 20px;
		line-height: 32px;
	}

	.picker,
	.picker2,
	input,
	.picker3 {
		border: 1px solid rgb(107, 103, 103);
		width: 60%;
		float: right;
		margin-right: 45px;
		border-radius: 6px;
		height: 32px;
		line-height: 32px;
	}

	.picker3 {
		width: 55%;
	}

	.input2 {
		width: 30%;
	}

	.input7 {
		width: 55%;
	}

	.input4 {
		width: 40%;
	}

	.input5 {
		width: 35%;
	}

	.input6 {
		width: 50%;
	}

	#editor {
		width: 90%;
		height: 100px;
		border: 1px solid rgb(32, 40, 150);
		margin-top: 10px;
	}

	.picker2 {
		width: 50%;
	}

	.title {
		margin-top: 20px;
		padding-bottom: 15px;
		font-size: 22px;
		color: rgb(42, 42, 155);
		display: flex;
		width: 100%;
		height: 60%;
		justify-content: center;
		align-items: center;
		border-bottom: 1px solid rgb(16, 55, 87);
	}

	.tijiao {
		margin: 10px 40px;
		background-color: aqua;
	}
</style>
