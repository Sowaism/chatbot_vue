<template>
	<div class="entry_input">
		<EntryInput :txtVal="txtVal" v-model="txtVal"/>
		<!-- <Button @click="addArrayMe()" :isDisabled="isDisabled"/> -->
		<Button @click="addArrayMe()" :isDisabled="isDisabled"/>
		{{isDisabled}}
		<!-- @click:JavaScript onclick属性と同様(イベントが発生したときに実行する関数を指定するための属性) -->
		<!-- 左：isDisabledは、子コンポーネントのpropで指定したもの-->
		<!-- 右：isDisabledは、現在のファイルのdataから取得した値を取得する-->
	</div>
</template>

<script>
import EntryInput from '../components/EntryInput.vue'
import Button from '../components/Button.vue'

export default {
	name: 'EntryParts',
	data:()=>({
			isDisabled : true,
			txtVal: '',
	}),
	// computed:{	
	// isDisabled:()=>(
	// 	this.txtVal === ''
	// ),
	// },
	components:{
		Button,
		EntryInput
	},
    methods:{
		// enterButtonFlag: function(){
		// if(this.txtVal !== ''){
		// 	this.isDisabled == false;
		// }
		// }
	// escapeHTML(string){
	// 	console.log('A')
	// 	return string.replace(/\&/g, '&amp;')
	// 	.replace(/\</g, '&lt;')
	// 	.replace(/\>/g, '&gt;')
	// 	.replace(/\"/g, '&quot;')
	// 	.replace(/\'/g, '&#x27');
	// },
	// enterButtonFlag:function(){
	// 	console.log('a');
	// 	if (txtVal == false) {
	// 		this.disabled = true;
	// 	} else {
	// 		this.disabled = false;
	// 	}
	// 	return;
	// }
	// addArrayMe:function() {
    //     chats.push({ player: true, txt: escapeHTML(txtVal()) });
    //     renderHTML();
    //     saveToLocalStorage();
    // }
	},
}
</script>

<style scoped>
/*menu*/
.entry_input{
	display: flex;
	width: 100%;
	z-index: 4;
}

.entry_input input{
	-webkit-appearance: none;
	-moz-appearance: none;
	appearance: none;
	border-top: none;
	border-left: 1px solid #CFD4D9;
	border-right: 1px solid #CFD4D9;
	border-bottom: none;
	width: 100%;
	font-size: 12px;
	outline: none;
	padding: 11px 4px;
}
</style>
