<template>
	<view id="detailsQuestionary">
		<view id="questionaryPromiseTitle">知情承诺书</view>
		<view id="questionaryPromiseText">
			本人已知悉自2021年9月起，吉首大学张家界学院有关问卷调查
			影响评奖评优、违纪处分、选拔交流等涉及学生切身利益的相关通知，
			将通过学工办微信公众号、易班平台、各班通知群（微信群或QQ群）、
			学工办公示栏以及红棉路经济与统计学院宣传栏进行公示。
		</view>
		<view id="questionaryPromiseEnd">
			本人承诺：因本人个人原因错过通知造成的一切后果，由本人自行承担。
		</view>
		<navigator id="questionaryPromiseButton" :url="nextUrl">
			<u-button type="primary" text="确定"/>
		</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				nextUrl:"/pages/fillQuestionary/index?id="
			}
		},
		onLoad(options) {
			this.nextUrl=this.nextUrl+options.id
			console.log(this.nextUrl);
		},
		methods: {

		},
	}
</script>

<style lang="less">
	#detailsQuestionary{
		display: flex;
		flex-flow: column;
		justify-content: flex-start;
		align-content: center;
		align-items: center;
		&::after{
			height: 80rpx;
			content: "";
		}
		#questionaryPromiseTitle{
			margin-top: 30rpx;
			font-size: 40rpx;
			font-weight: bold;
			color: #3399ff;
		}
		#questionaryPromiseText{
			padding: 30rpx;
			font-size: 30rpx;
		}
		#questionaryPromiseEnd{
			padding: 30rpx ;
			font-weight: bold;
		}
		#questionaryPromiseButton{
			position: fixed;
			bottom: 0;
			width: 750rpx;
		}
	}
	
</style>
