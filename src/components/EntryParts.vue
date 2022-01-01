<template>
	<div class="entry_input">
		<!-- <EntryInput :txtVal="txtVal" @input="txtVal = $event.target.value"/> これでも書けます！ -->
		<EntryInput
		v-model:txtVal="txtVal"
		/>
		<Button
		@click="addItem"
		:isDisabled="isDisabled"
		/>
		<!-- <div v-for="(chat,index) in chats" :key="index">
		{{chat.me.txt}}
		</div> -->
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
	data:()=>({ //dataだけは、アロー関数で記述できます
			txtVal: '',
			player:true,
	}),
	inject: ['chats'],
	computed:{
		isDisabled:function() {
		return this.txtVal === ''
	},
	},
	components:{
		Button,
		EntryInput
	},
    methods:{
		addItem:function(){
			// this.chats.innerHTML = '';
			let chat ={
				me: {player: true, txt:this.txtVal}
			}
			this.chats.push(chat); //配列にmeのメッセージを入れる
			console.log(this.chats);
			this.txtVal = '' //入力後、文字列を空にする
		}
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
