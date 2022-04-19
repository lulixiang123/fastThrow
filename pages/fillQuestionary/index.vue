<template>
	<view id="fillQuestionary">
		<view id="questionaryName">{{questionary.questionName}}</view>
		<view id="questionaryProblems">
			<view class="questionaryProblem">
				<template v-for="(item,index) in problemList">
					<view class="questionaryProblemItem">
						<view class="ProblemMessage">
						    Q{{index+1}}【{{item.problemType}}】{{item.problemName}}
						</view>
						<view class="ProblemContent">
						   <template v-if="item.problemType==='单选题'">
							   <SingleChoiceQuestions :problemId="item.problemId"  @setSelect="setSelect"/>
						   </template>
						   <template v-else-if="item.problemType==='多选题'">
							   <multipleChoiceQuestions :problemId="item.problemId" @setSelect="setSelect"/>
						   </template>
						   <template v-else-if="item.problemType==='填空题'">
							   <fillBlankQuestions :problemId="item.problemId" @setSelect="setSelect"/>
						   </template>
						</view>
					</view>
				</template>
			</view>
		</view>
		<view v-if="nowSuccess===problemList.length" id="questionarySubmitButton">
			<u-button type="primary" text="提交问卷" @click="questionaryComplete"/>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				problemList:[{
					ProblemId:0,
					ProblemName:"问题名字",
					ProblemType:"题型"
				}],
				questionary:{
					questionId:20225731,
					questionName:"问卷名称",
					questionState:"已经开始",
					questionRange:"理工农学院",
					questionStartTime:"2018-8-27 9:00",
					questionEndTime:"2018-8-27 18:00",
					questionAllFill:577,
					questionCompleteFill:0
				},
				answerList:[],
				nowSuccess:0
			}
		},
		onLoad() {
			//获取问卷信息
			this.getQuestionaryMessage()
			//获取问题信息
			this.getProblemMessage()
			
		},
		methods: {
			//获取问卷信息
			getQuestionaryMessage(){
				//获取问卷信息
				//传参: questionId
				// 返回: Array<{
				// 	questionId:Number,questionName:String,questionState:String
				// 	questionRange:String,questionStartTime:String,questionEndTime:String,
				// 	questionAllFill:Number,questionCompleteFill:Number
				// }>
				this.questionary={
					questionId:20225731,
					questionName:"问卷名称",
					questionState:"已经开始",
					questionRange:"理工农学院",
					questionStartTime:"2018-8-27 9:00",
					questionEndTime:"2018-8-27 18:00",
					questionAllFill:577,
					questionCompleteFill:0
				}
			},
			getProblemMessage(){
				//获取问题信息
				//传参: questionId
				//返回: Array<{problemId:Number,problemName:String,problemType:String}>
				this.problemList=[
					{
						problemId:0,
						problemName:"问题名字",
						problemType:"单选题"
					},{
						problemId:1,
						problemName:"问题名字",
						problemType:"多选题"
					},{
						problemId:2,
						problemName:"问题名字",
						problemType:"填空题"
					}
				]
			},
			//获取子组件传来的答案
			setSelect(newSelect){
				let i
				for(i=0;i<this.answerList.length;i++)
				{
					if(this.answerList[i].problemId===newSelect.problemId){
						this.answerList.splice(i,1,newSelect)
						break
					}
				}
				if(i===this.answerList.length){
					this.answerList.push(newSelect)
				}
				this.nowSuccess=0
				for(let j=0;j<this.answerList.length;j++){
					if(this.answerList[j].selectId.length!=0||this.answerList[j].selectTextarea!=""){
						this.nowSuccess=this.nowSuccess+1
					}
				}
			},
			//提交问卷
			questionaryComplete(){
				//传入参数: answerList:Array<{problemId:Number,selectId:Array<Number>,selectTextarea:String}>,questionId:Number,userId:Number
				//返回值: 无
				
				//回调函数success
				uni.navigateTo({url:"/pages/fillQuestionary/success"})
				//回调函数error
				// uni.navigateTo("/pages/myQuestionary/error")
			}
		}
	}
</script>

<style lang="less">
	#fillQuestionary{
		display: flex;
		flex-flow: column;
		justify-content: center;
		align-content: center;
		align-items: center;
		padding: 20rpx 0;
		&::after{
			height: 80rpx;
			content: "";
		}
		#questionaryName{
			font-size: 48rpx;
			font-weight: bold;
			color: #3399ff;
		}
		#questionaryProblems{
			width: 700rpx;
			.questionaryProblem{
				margin: 20rpx 0;
				.questionaryProblemItem{
					margin-top: 64rpx;
				}
				.ProblemMessage{
					font-size: 36rpx;
					font-weight: bold;
					color: #3399ff;
				}
				.ProblemContent{
					margin-top: 12rpx;
				}
			}
		}
		#questionarySubmitButton{
			position: fixed;
			bottom: 0;
			width: 750rpx;
		}
	}
</style>
