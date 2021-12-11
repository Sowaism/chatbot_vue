<template>
	<button id="addbtn" class="inquiry-next-btn" @click="addBtn()" :disabled="isDisabled">送信</button>
</template>

<script>
export default {
	name: 'Button',
	data:function() {
	return{
		isDisabled:true,
		value:'',
	}
  },
	methods:{
		addBtn:function(){
			this.isDisabled = true;
		},
	// 	enterButtonFlag:function() {
    //     if (txtVal() == false) {
    //         this.addBtn.disabled = true;
    //     } else {
    //         this.addBtn.disabled = false;
    //     }
    //     return;
    // },
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
