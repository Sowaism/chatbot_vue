<template>
	<div class="entry_input">
		<EntryInput :txtVal="txtVal"/>
		<!-- <Button @click="addArrayMe()" :isDisabled="isDisabled"/> -->
		<Button :isDisabled="isDisabled"/>
		<!-- {{isDisabled}} -->
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
			// isDisabled : true,
			txtVal: '',
	}),
	computed:{	
	isDisabled:()=>(
		this.txtVal === ''
	),
	},
	components:{
		Button,
		EntryInput
	},
    methods:{
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
