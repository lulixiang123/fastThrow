<template>
	<view id="error">
		<view id="errorIcon">
			<u-icon name="error-circle" size="500rpx" color="red"/>
			<view id="errorText">提交失败,返回主页</view>
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
	#error{
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		#errorIcon{
			border-radius: 250rpx;
			#errorText{
				text-align: center;
				color: red;
				font-size: 56rpx;
				font-weight: bold;
				letter-spacing: 5rpx;
			}
		}
	}
</style>