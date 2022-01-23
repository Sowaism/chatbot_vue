<template>
	<div :class="isPlayer">
		<p>{{iconTxt}}</p>
			<div>
				<img
				:src="iconSrc"
				:alt="iconAlt"
				width="40"
				height="40"
				>
			</div>
	</div>
</template>

<script>
// import assets from "@/assets/me.jpg";

export default {
	name: 'MessageRender',
	props: ['chat','txtVal'], //App.vueのデータを扱う
	data:()=>({
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
			return this.chat.sender ? require('@/assets/me.jpg'): require('@/assets/you.jpg');
		},
		iconAlt(){
			return this.chat.sender ? '自分の画像': '相手の画像';
		},
		iconTxt(){
			return this.chat.sender ? this.chat.txt: this.randomMessage();
		},
		isPlayer(){
			// console.log(this.chat.sender);
			return this.chat.sender ? 'my_message': 'you_message'
		},
	},
	methods:{
		randomMessage(){
			// console.log(Math.floor(Math.random() * this.randomTxt.length));
			const randomValue = Math.floor(Math.random() * this.randomTxt.length);
			this.randomTxt[randomValue];
			console.log(this.randomTxt[randomValue]);
		}
	},
	emit:['randomTxt'],
}
</script>

<style scoped>
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
	order: 2;
}
.you_message div{
	order: 1;
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
