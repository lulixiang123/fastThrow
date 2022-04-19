<template>
	<view id="fillBlankQuestions">
		<u--textarea v-model="textareaValue" :placeholder="selectList[0].selectContent" autoHeight count maxlength="100" @input="textareaInput"/>
	</view>
</template>

<script>
	export default {
		props:{
			problemId:{
				type: Number,
				default: 0,
			}
		},
		data() {
			return {
				selectList:[
					{
						selectId:8,
						selectContent:"请输入"
					}
				],
				textareaValue:""
			}
		},
		onLoad() {
			this.getSelectList()
		},
		methods: {
			textareaInput(){
				this.$emit("setSelect",{
					problemId:this.problemId,
					selectId:[this.selectList[0].selectId],
					selectTextarea:this.textareaValue
				})
			},
			getSelectList(){
				//获取问题选项
				//传参 problemId
				//返回 selectList:<{selectId:Number,selectContent:String}>
			}
		},
	}
</script>

<style lang="less">
	
</style>
