<template>
	<navigator :url=routerName>
		<view class="questionThumbnail">
			<view class="questionaryName">{{questionName}}</view>
			<view class="questionTime">
			{{questionStartTime}} 至 {{questionEndTime}}
			</view>
			<view class="questionRange">参与范围 : {{questionRange}}</view>
			<view class="questionPeople">
				<view class="questionAllFill">总参与数 : {{questionAllFill}}</view>
				<view class="questionCompleteFill">从完成数 : {{questionCompleteFill}}</view>
			</view>
		</view>
	</navigator>
</template>

<script>
	export default {
		props:{
			questionId:{
				type: Number,
				default: 0,
			},
			questionName:{
				type: String,
				default: "问卷名称",
			},
			questionState:{
				type: String,
				default: "已经开始",
			},
			questionRange:{
				type: String,
				default: "理工农学院",
			},
			questionStartTime:{
				type: String,
				default: "2018-8-27 9:00",
			},
			questionEndTime:{
				type: String,
				default: "2018-8-27 18:00",
			},
			questionAllFill:{
				type: Number,
				default: 1271,
			},
			questionCompleteFill:{
				type: Number,
				default: 277,
			}
		},
		data() {
			return {
			}
		},
		onLoad() {

		},
		methods: {

		},
		computed:{
			routerName(){
				return "/pages/detailsQuestionary/index?id="+this.questionId
			}
		}
	}
</script>

<style lang="less">
	.questionThumbnail{
		width: 700rpx;
		height: 320rpx;
		margin: 40rpx 0;
		color: black;
		border-radius: 20rpx;
		background-color: white;
		.questionaryName{
			height: 120rpx;
			padding:10rpx 40rpx;
			font-size: 32rpx;
			font-weight: bold;
			background-color: #3399ff;
			color: white;
			border-top-left-radius: 20rpx;
			border-top-right-radius: 20rpx;
			display: flex;
			align-items: center;
			align-content: center;
		}
		.questionTime{
			height: 60rpx;
			line-height: 60rpx;
			font-size: 28rpx;
			text-align: center;
		}
		.questionRange{
			height: 60rpx;
			line-height: 60rpx;
			font-size: 28rpx;
			text-align: center;
		}
		.questionPeople{
			height: 60rpx;
			font-size: 26rpx;
			display: flex;
			align-items: center;
			justify-content: space-around;
		}
	}
</style>
