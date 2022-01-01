<template>
	<div id="message_area" class="message_area">
		<ul>
			<UserMeParts :userMessage="userMessage" :value="this.txtVal"/>
			<UserYouParts/>
			{{botTxts}}
		</ul>
	</div>
</template>

<script>
import UserMeParts from '../components/UserMeParts.vue'
import UserYouParts from '../components/UserYouParts.vue'

export default {
	name: 'UserList',
	data:()=>({
		userMessage:'aa',
	}),
	inject: ['chats'],
	computed:{
		// meMessage:function() {
		// 	return this.userMessage === ''
		// },
	},
	methods:{
		// entryText: function () {
		// 	this.userMessage = this.chats.me.txt
		// }
	},
	components:{
		UserMeParts,
		UserYouParts
	}
}
</script>

<style scoped>
ul{
	margin: 0 auto;
	padding: 0;
	width:300px;
}
#message_area {
	height: calc(100vh - 36px);
	overflow: scroll;
}
</style>
