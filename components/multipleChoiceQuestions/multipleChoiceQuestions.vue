<template>
	<view id="multipleChoiceQuestions">
		<u-checkbox-group v-model="checkboxValue" placement="column" @change="checkboxChange">
		    <u-checkbox :customStyle="{marginBottom: '12px'}" v-for="(item, index) in selectList" :key="item.selectId" :label="item.selectContent" :name="item.selectId" />
		</u-checkbox-group>
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
						selectId:4,
						selectContent:"选项A"
					},
					{
						selectId:5,
						selectContent:"选项B"
					},
					{
						selectId:6,
						selectContent:"选项C"
					},
					{
						selectId:7,
						selectContent:"选项D"
					},
				],
				checkboxValue:[]
			}
		},
		onLoad() {
			this.getSelectList()
		},
		methods: {
			checkboxChange(n){
				this.$emit("setSelect",{
					problemId:this.problemId,
					selectId:n,
					selectTextarea:""
				})
			},
			getSelectList(){
				//获取问题选项
				//传参 problemId
				//返回 selectList:<{selectId:Number,selectContent:String}>
			}
		}
	}
</script>

<style lang="less">
	
</style>
