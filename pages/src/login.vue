<template>
  <div class="app-login content">
	  <view><p class="title">{{ title }}</p></view>
    <view>
      <label for="user" class="float" >用户名：</label>
      <input type="text" id="user" :value="userVal" @focus="show" @blur="noshow"/>
    </view>

    <view>
      <label for="password" class="float">密&nbsp;&nbsp;&nbsp;码：</label>
      <input type="text" id="password" :value="passVal" @focus="showPass" @blur="noshowPass"/>
    </view>

    <view>
        <button class="btn" @click="submit()">登&nbsp;&nbsp;录</button>
    </view>
  </div>
</template>

<script>
export default {
  setup() {},
  onLoad(){
  	  this.getMsg()
  },
  data(){
      return {
		   title: "食品安全检测管理系统",
          userVal:"请输入用户名",
          passVal:"请输入密码"
      }
  },
  onLoad(options){
	  if(options.item){
		   const editItem = JSON.parse(decodeURIComponent(options.item));
	  }
	  this.getMsg()
  	},
  methods:{
	  
			 getMsg(){
	  		  const db = uniCloud.database() //创建数据库链接
	  		  db.collection("user").get() // 获取数据表信息
	  		  .then(res => {
	  			  console.log(res)
	  		  }).catch(err => {
	  			  console.log(err)
	  		  }) 
	  	  },
		
	      show(e){
	          if(e.detail.value===this.userVal){
	              this.userVal=''
	              
	          }
	      },
	      noshow(e){
	          if(e.detail.value===""){
	              this.userVal='请输入用户名'
	          }
	      },
	      showPass(e){
	          if(e.detail.value===this.passVal){
	              this.passVal=''
	              
	          }
	      },
	      noshowPass(e){
	          if(e.detail.value===""){
	              this.passVal='请输入密码'
	          }
	      },
	      submit(){
	        console.log(11)
	        uni.switchTab({
	        	url:"./collection"
	        })
	      }
	  }
	  
};
</script>

<style scoped>
.content {
  		flex: auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
}
input{
    border: 1rpx solid #000;
		height: 30px;
		margin: 20px 20px;
		line-height: 30px;
		color: rgb(44, 40, 37);
		width: 70%;
		display: flex;
		justify-content: center;
		align-items: center;
        background-color: aliceblue;
}

label{
    font-size: 18px;
    color: aliceblue;
}
.float{
    float:left;
	margin-top: 22px;
}
.btn{
    margin: 40px 0px;
    background-color: rgb(8, 132, 233);
    color:#fff;
}
.title{
	padding: 130px 0px 30px 0px;
	font-size: 28px;
	color: white;
}

</style>

<style>
	page{
		background-color: rgb(33, 40, 109);
	}
</style>