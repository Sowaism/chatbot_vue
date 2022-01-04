<template>
	<div id="message_area" class="message_area">
		<ul>
			<!-- <UserMeParts :txtVal="txtVal" @input="$emit('update:txtVal', $event.target.value)"/> -->
			<li>
				<div class="my_message">
					<p>{{txtVal}}</p>
					<div><img src="../assets/me.jpg" width="40" height="40" alt="自分の画像"></div>
				</div>
			</li>
			<li>
				<div class="you_message">
					<div><img src="../assets/you.jpg" width="40" height="40" alt="相手の画像"></div>
					<div><p>後から処理を適用します。</p></div>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'UserList',
	props: ['chats'], //App.vueのデータを扱う
	data:()=>({
		botTxts : [
		'こんにちは！メッセージありがと〜！',
		'元気？僕は元気だよー！',
		'いえ〜い！！',
		'僕はチャットボットのマークだよ！',
		'...',
		'大吉！',
		],
	}),
	computed:{
		// meMessage:function() {
		// },
	},
	methods:{
		// entryText: function () {
		// 	this.userMessage = this.chats.me.txt
		// }
	// addItem() {
    //   this.$emit('addBtn', 'hi from child');
    // },
	},
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
