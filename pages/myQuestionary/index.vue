<template>
	<view id="myQuestionary">
		<view id="myQuestionarySearch">
			<u-search id="myQuestionarySearchInput" placeholder="请输入问卷名称" v-model="searchText" :clearabled="true" :show-action="false" @search="questionarySearch()"/>
			
		</view>
		<view id="myQuestionaryArea">
			<template v-for="item in questionItems">
				<questionThumbnail
				 :questionId="item.questionId" :questionName="item.questionName"
				 :questionState="item.questionState" :questionRange="item.questionRange"
				 :questionStartTime="item.questionStartTime" :questionEndTime="item.questionEndTime"
				 :questionAllFill="item.questionAllFill" :questionCompleteFill="item.questionCompleteFill" />
			</template>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchText:"",
				questionItems:[{
					questionId:20225731,
					questionName:"问卷名称",
					questionState:"已经开始",
					questionRange:"理工农学院",
					questionStartTime:"2018-8-27 9:00",
					questionEndTime:"2018-8-27 18:00",
					questionAllFill:1271,
					questionCompleteFill:277
				}]
			}
		},
		onLoad() {
			
			this.getQuestionary()
		},
		
		methods: {
			//请求用户所有问卷
			//传入参数: userId
			//返回值: Array<{questionId:number,questionName:string,......}>
			getQuestionary(){
			},
			//搜索用户问卷
			//传入参数: searchText,userId
			//返回值: Array<{questionId:number,questionName:string,......}>
			questionarySearch(){
				
			}
		}
	}
</script>

<style lang="less">
	#myQuestionary{
		display: flex;
		flex-flow: column;
		justify-content: center;
		align-content: center;
		align-items: center;
		background-color: #F1F2F7;
		
		#myQuestionarySearch{
			background-color: #3399ff;
			width: 650rpx;
			padding:20rpx 50rpx;
		}
	}
	
</style>
