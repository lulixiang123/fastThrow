<template>
	<view id="SingleChoiceQuestions">
		<u-radio-group v-model="radioValue" placement="column" @change="groupChange">
		    <u-radio :customStyle="{marginBottom: '12px'}" v-for="(item, index) in selectList" :key="item.selectId" :label="item.selectContent" :name="item.selectId" />
		</u-radio-group>
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
						selectId:0,
						selectContent:"选项A"
					},
					{
						selectId:1,
						selectContent:"选项B"
					},
					{
						selectId:2,
						selectContent:"选项C"
					},
					{
						selectId:3,
						selectContent:"选项D"
					}
				],
				radioValue:""
			}
		},
		onLoad() {
			this.getSelectList()
		},
		methods: {
			groupChange(n) {
				this.$emit("setSelect",{
					problemId:this.problemId,
					selectId:[n],
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
