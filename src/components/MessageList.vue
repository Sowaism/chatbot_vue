<template>
	<div id="message_area" class="message_area">
		<ul>
			<li v-for="chat in chats" :key="chat">
				<MessageRender
				:chat="chat"
				:player="player"
				:txtVal="txtVal"
				/>
			</li>
		</ul>
	</div>
</template>

<script>
import MessageRender from '../components/MessageRender.vue'

export default {
	name: 'MessageList',
	props: ['chats','txtVal','player'], //App.vueのデータを扱う
	data:()=>({
		// isPlayer:this.player,
	}),
	computed:{
	},
	methods:{
		isPlayer:function(){
			console.log(this.player);
			return this.player ? 'my_message': 'you_message'
		},
		// isAltEmit() {
		// 	this.$emit('isAlt')
		// 	},
	},
	components:{
		MessageRender,
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
li{
	list-style: none;
}
.my_message{
	display: flex;
	justify-content:flex-end;
	align-items: center;
	margin:0 4px;
}
.my_message p{
	max-width: 65%;
	background-color: #CED4DA;
	border-radius: 10px;
	padding: 6px 6px;
	margin-left: 8px;
	margin-right: 8px;
	position: relative;
	z-index: 3;
}
.my_message p:before {
	content: "";
	position: absolute;
	top: 2px;
	right: -14px;
	border: 8px solid transparent;
	border-left: 18px solid #CED4DA;
	-webkit-transform: rotate(-35deg);
	transform: rotate(-35deg);
	z-index: -1;
}
.you_message  {
	display: flex;
	justify-content:flex-start;
	align-items: center;
	margin:0 4px;
}
.you_message p {
	max-width: 65%;
	background-color: #CED4DA;
	border-radius: 10px;
	padding: 6px 6px;
	margin-left: 8px;
	margin-right: 8px;
	position: relative;
	z-index: 3;
}
.you_message p:before{
	content: "";
	position: absolute;
	top: 2px;
	left: -14px;
	border: 8px solid transparent;
	border-right: 18px solid #CED4DA;
	-webkit-transform: rotate(35deg);
	transform: rotate(35deg);
	z-index: -1;
}
img{
	border-radius: 20px;
}
</style>
