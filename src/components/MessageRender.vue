<template>
	<li>
		<div :class="isPlayer()">
			<p>{{iconTxt}}</p>
			<div>
				<!-- :alt="this.$emit('isAlt')" -->
				<img
				:src="iconSrc"
				:alt="iconAlt"
				width="40"
				height="40"
				>
			</div>
		</div>
	</li>
	<!-- <li>
		<div class="you_message">
			<div><img src="@/assets/you.jpg" width="40" height="40" alt="相手の画像"></div>
			<div><p>後から処理を適用します。</p></div>
		</div>
	</li> -->
</template>

<script>
// import assets from "@/assets/me.jpg";

export default {
	name: 'MessageRender',
	props: ['chat','txtVal','player'], //App.vueのデータを扱う
	data:()=>({
		// renderPlayer:this.player,
		randomTxt : [
		'こんにちは！メッセージありがと〜！',
		'元気？僕は元気だよー！',
		'いえ〜い！！',
		'僕はチャットボットのマークだよ！',
		'...',
		'大吉！',
		],
	}),
	computed:{
		iconSrc(){
			return this.chat.player ? require('@/assets/me.jpg'): require('@/assets/you.jpg');
		},
		iconAlt(){
			return this.chat.player ? '自分の画像': '相手の画像';
		},
		iconTxt(){
			return this.chat.player ? this.chat.txt: this.randomTxt;
		},
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
	emit:['randomTxt'],
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
