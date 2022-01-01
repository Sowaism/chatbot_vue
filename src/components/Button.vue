<template>
	<button
	id="addbtn"
	:disabled="isDisabled"
	>
	送信
	</button>
</template>

<script>
export default {
	name: 'Button',
	props:{
		isDisabled:{ //HTMLに標準で存在する属性と同様の名前は使用NG（トラブルの原因になる）
			type:Boolean,
			default:true,
		}
	},
}
</script>

<style scoped>
#addbtn{
	background-color: #001d47;
	color: #fff;
	border: none;
	cursor: pointer;
	outline: none;
	padding: 0;
	appearance: none;
	width: 48px;
}

#addbtn:disabled{
	background-color: #65717e;
}
</style>
