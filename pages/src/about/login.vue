<!-- <template>
  <div class="app-login">
    <view>
      <label for="user" class="float" >用户名：</label>
      <input type="text" id="user" :value="userVal" @focus="show" @blur="noshow"/>
    </view>

    <view>
      <label for="password" class="float">密&nbsp;&nbsp;&nbsp;码：</label>
      <input type="text" id="password" :value="passVal" @focus="showPass" @blur="noshowPass"/>
    </view>

    <view>
        <button class="btn" @click="navgateTo()">登&nbsp;&nbsp;录</button>
    </view>
  </div>
</template>

<script>
export default {
  setup() {},
  data(){
      return {
          userVal:"请输入用户名",
          passVal:"请输入密码"
      }
  },
  methods:{
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
      navgateTo(){
        uni.switchTab({
        	url:"./collection"
        })
      }
  }
};
</script>

<style scoped>
input{
    border: 1rpx solid #000;
		height: 30px;
		margin: 20px 20px;
		line-height: 30px;
		color: rgb(26, 22, 22);
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
}
.btn{
    margin: 40px 0px;
    background-color: rgb(8, 132, 233);
    color:#fff;
}

</style> -->