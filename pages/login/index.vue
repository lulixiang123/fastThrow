<template>
	<view id="login">
		<view id="form">
			<u-text id="formTitle" type="primary" text="用户登录" size="64rpx" align="center"></u-text>
			<u--input v-model="sId" class="formInput" placeholder="请输入学号" border="bottom" clearable />
			<u--input v-model="sPassword" class="formInput" placeholder="请输入密码" border="bottom" clearable />
			<u-alert v-if="tipShow" id="formTip" title="忘记密码？" type = "warning" description = "你或许需要寻求辅导员或专业老师重置密码"/>
			<u-button id="formButton" type="primary" text="确定" @click="studentLogin"/>
		</view>
		 
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sId:"",
				sPassword:"",
				tipShow:true
			}
		},
		onLoad() {

		},
		methods: {
			studentLogin(){
				//登录
				//传参 this.sId,this.sPassword
				//返回 token
				uni.reLaunch({url:"/pages/myQuestionary/index"})
			}
		}
	}
</script>

<style lang="less">
	#login{
		display: flex;
		flex-flow: column;
		justify-content: center;
		align-content: center;
		align-items: center;
		padding: 20rpx 0;
		#form{
			width: 600rpx;
			margin-top: 20vh;
			#formTitle{
				
			}
			.formInput{
				margin-top: 20rpx;
			}
			#formTip{
				margin-top: 20rpx;
			}
			#formButton{
				margin-top: 40rpx;
			}
		}
	}
</style>
