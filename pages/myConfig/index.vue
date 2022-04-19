<template>
	<view id="fillQuestionary">
		<u-popup :show="changePasswordShow" mode="center"  @close="changePasswordAreaClose">
			<view id="changePasswordShowAreaTitle">密码修改</view>
		    <view id="changePasswordShowAreaContent">
				 <u--input
				  placeholder="请输入老密码" border="bottom" v-model="oldPassword"/>
		         <u--input
				 placeholder="请输入新密码" border="bottom" v-model="newPassword"/>
		    </view>
			<view id="changePasswordShowAreaButtons">
				<u-button type="primary" @click="changeUserPassword">确认</u-button>
				<u-button type="primary" @click="changePasswordShow=!changePasswordShow">取消</u-button>
			</view>
		</u-popup>
		<u-cell-group>
			<u-cell :value="userMessage.userId">
				<u-icon slot="icon" size="32" name="fingerprint" color="#3399ff"/>
				<text slot="title" class="mineBottomItemText">学号</text>
			</u-cell>
			<u-cell :value="userMessage.username">
				<u-icon slot="icon" size="32" name="github-circle-fill" color="#3399ff"/>
				<text slot="title" class="mineBottomItemText">名称</text>
			</u-cell>
			<u-cell :value="userMessage.userGroup">
				<u-icon slot="icon" size="32" name="list-dot" color="#3399ff"/>
				<text slot="title" class="mineBottomItemText">所属</text>
			</u-cell>
			<u-cell :isLink="true" @click="changePasswordShow=!changePasswordShow">
				<u-icon slot="icon" size="32" name="lock-fill" color="#3399ff"/>
				<text slot="title" class="mineBottomItemText">修改密码</text>
			</u-cell>
			<u-cell>
				<u-icon slot="icon" size="32" name="close-circle-fill" color="#3399ff"/>
				<text slot="title" class="mineBottomItemText" @click="userOut">退出账户</text>
			</u-cell>
		</u-cell-group>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userMessage:{
					userId:"学号",
					username:"名称",
					userGroup:"学院-专业-班级"
				},
				changePasswordShow:false,
				oldPassword:"",
				newPassword:""
			}
		},
		onLoad() {
			this.getUserMessage()
		},
		methods: {
			changePasswordAreaClose(){
				console.log(1)
				this.changePasswordShow=false
			},
			getUserMessage(){
				//搜索用户信息
				//传参: token
				//返回: userMessage={userId:string,username:string,userGroup:string}
			},
			changeUserPassword(){
				//修改用户密码
				//传参: token
				//返回: userMessage={userId:string,username:string,userGroup:string}
				this.changePasswordShow=!this.changePasswordShow
			},
			userOut(){
				//uni.removeStorageSync("token")
				uni.reLaunch({url:"/pages/login/index"})
			}
		}
	}
</script>

<style lang="less">
	#fillQuestionary{
		background-color: #F1F2F7;
		height: 100vh;
	}
	#changePasswordShowAreaTitle{
		background-color: #3399ff;
		padding: 20rpx 0;
		text-align: center;
		color: white;
		font-size: 36rpx;
		font-weight: bold;
	}
	#changePasswordShowAreaContent{
		padding: 50rpx 100rpx;
	}
	#changePasswordShowAreaButtons{
		display: flex;
	}
</style>
