<template>
	<div>
		<li>
			<div class="you_message">
				<div>
					<img src="../assets/you.jpg" width="40" height="40" alt="相手の画像">
				</div>
				<div>
					<!-- <p>{{random()}}</p> -->
					<p>後から処理を適用します。</p>
				</div>
			</div>
		</li>
	</div>
</template>

<script>

export default {
	name: 'UserYouParts',
	// props: [botTxts],
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
	// methods:{
	// random:function(){
	// 	console.log('test');
	// 	const random = Math.floor(Math.random() * this.botTxts.length);
	// 	return this.botTxts[random];
	// }
	// }
	// emits:['update:botTxts']
}
</script>

<style scoped>
li{
	list-style: none;
}
.you_message {
	display: flex;
	justify-content:flex-start;
	align-items: center;
	margin:0 4px;
}
p {
	max-width: 65%;
	background-color: #CED4DA;
	border-radius: 10px;
	padding: 6px 6px;
	margin-left: 8px;
	margin-right: 8px;
	position: relative;
	z-index: 3;
}
p:before{
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
