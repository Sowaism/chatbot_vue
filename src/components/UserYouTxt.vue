<template>
    <div>
		<p v-for="botTxt in botTxts" :key="botTxt">
			{{botTxt}}
		</p>
	</div>
</template>

<script>
export default {
  name: 'UserYouImg',
  data:	function() {
	return{
		chats : [],
		botTxts : [
		'こんにちは！メッセージありがと〜！',
		'元気？僕は元気だよー！',
		'いえ〜い！！',
		'僕はチャットボットのマークだよ！',
		'...',
		'大吉！',
		]
	}
  },
  methods:{
	random:function(){
		console.log('7');
	}
  }
}
</script>

<style scoped>
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
</style>
