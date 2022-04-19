<template>
	<view id="success">
		<view id="successIcon">
			<u-icon name="checkmark-circle" size="500rpx" color="#00C9A7"/>
			<view id="successText">提交成功,返回主页</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			console.log(1)
			this.backHome()
		},
		methods: {
			backHome(){
				setTimeout(()=>{
					uni.reLaunch({url:"/pages/myQuestionary/index"})
				},3000)
			}
		}
	}
</script>

<style lang="less">
	#success{
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		#successIcon{
			border-radius: 250rpx;
			#successText{
				text-align: center;
				color: #00C9A7;
				font-size: 56rpx;
				font-weight: bold;
				letter-spacing: 5rpx;
			}
		}
	}
</style>
