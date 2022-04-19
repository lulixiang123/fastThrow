<template>
	<view id="fillQuestionary">
		<view id="questionaryName">{{questionary.questionName}}</view>
		<view id="questionaryProblems">
			<view class="questionaryProblem">
				
				<view class="ProblemMessage">
				    {{problem[nowIndex].ProblemSort}}.({{problem[nowIndex].ProblemType}}) {{problem[nowIndex].ProblemName}}
				</view>
				
				<view class="ProblemContent">
					<template v-if="problem[nowIndex].ProblemType==='单选题'">
						<u-radio-group v-model="radioValue" placement="column">
						    <u-radio :customStyle="{marginBottom: '8px'}"  v-for="(item, index) in problem[nowIndex].ProblemOption" :key="index" :label="item" :name="item" />
						</u-radio-group>
					</template>
					<template v-else-if="problem[nowIndex].ProblemType==='多选题'">
						<u-checkbox-group v-model="checkboxValue" placement="column">
						    <u-checkbox :customStyle="{marginBottom: '8px'}" v-for="(item, index) in problem[nowIndex].ProblemOption" :key="index" :label="item" :name="item" />
						</u-checkbox-group>
					</template>
					<template v-else-if="problem[nowIndex].ProblemType==='填空题'">
						<u--textarea v-model="textareaValue" placeholder="请输入..." autoHeight count maxlength="100"/>
					</template>
				</view>
				
			</view>
			<view id="questionaryProblemsBtns">
				<template v-if="nowIndex!==problem.length-1">
					<u-button type="primary" text="下一题" @click="nowIndexNext()"/>
				</template>
				<template v-else>
					<u-button type="primary" text="完成" @click="questionaryComplete()"/>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				problem:[{
					ProblemId:0,
					ProblemName:"问题名字",
					ProblemSort:1,
					ProblemType:"单选题",
					ProblemOption:["单选项A","单选项B","单选项C","单选项D"]
				},{
					ProblemId:1,
					ProblemName:"问题名字",
					ProblemSort:2,
					ProblemType:"多选题",
					ProblemOption:["多选项A","多选项B","多选项C","多选项D"]
				},{
					ProblemId:2,
					ProblemName:"问题名字",
					ProblemSort:3,
					ProblemType:"填空题",
					ProblemOption:[]
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
				nowIndex:0,
				radioValue:"",
				checkboxValue:[],
				textareaValue:"",
				answer:[]
			}
		},
		onLoad() {

		},
		methods: {
			//保存问题答案
			ProblemPreserve(){
				let success=false
				console.log(this.problem[this.nowIndex].ProblemId)
				
				if(this.problem[this.nowIndex].ProblemType==='单选题'&&this.radioValue.length!=0){
					this.answer[this.nowIndex]={problemId:this.problem[this.nowIndex].ProblemId,value:this.radioValue}
					success=true
					this.radioValue=""
				}
				else if(this.problem[this.nowIndex].ProblemType==='多选题'&&this.checkboxValue.length!=0){
					this.answer[this.nowIndex]={problemId:this.problem[this.nowIndex].ProblemId,value:this.checkboxValue}
					success=true
					this.checkboxValue=""
				}
				else if(this.problem[this.nowIndex].ProblemType==='填空题'&&this.textareaValue.length!=0){
					this.answer[this.nowIndex]={problemId:this.problem[this.nowIndex].ProblemId,value:this.textareaValue}
					success=true
					this.textareaValue=""
				}
				return success
			},
			//下一题
			nowIndexNext(){
				this.ProblemPreserve()
				this.nowIndex=this.nowIndex+1
			},
			//提交问卷
			questionaryComplete(){
				this.ProblemPreserve()
				//传入参数: answer:Array<{problemId:Number,value:any}>,questionId:Number,userId:Number
				//返回值: 无
				console.log(this.answer,this.questionId,this.userId)
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
		#questionaryName{
			font-size: 48rpx;
			font-weight: bold;
			color: #3399ff;
		}
		#questionaryProblems{
			width: 700rpx;
			margin-top: 30rpx;
			.questionaryProblem{
				margin: 20rpx 0;
				.ProblemMessage{
					font-size: 36rpx;
					font-weight: bold;
					color: #3399ff;
				}
				.ProblemContent{
					margin-top: 20rpx;
				}
			}
			#questionaryProblemsBtns{
				position: fixed;
				bottom: 0;
				width: 700rpx;
			}
		}
	}
</style>
