<template>
	<div>
		<li>
			<div class="my_message">
				<p>{{userMessage}}</p>
				<div>
					<img src="../assets/me.jpg" width="40" height="40" alt="自分の画像">
				</div>
			</div>
		</li>
	</div>
</template>

<script>

export default {
	name: 'UserMeParts',
	props:{
		userMessage:{ //HTMLに標準で存在する属性と同様の名前は使用NG（トラブルの原因になる）
			type:String,
			default:'',
	}
	},
	methods:{
	}
}
</script>

<style scoped>
li{
	list-style: none;
}
.my_message{
	display: flex;
	justify-content:flex-end;
	align-items: center;
	margin:0 4px;
}
p{
	max-width: 65%;
	background-color: #CED4DA;
	border-radius: 10px;
	padding: 6px 6px;
	margin-left: 8px;
	margin-right: 8px;
	position: relative;
	z-index: 3;
}
p:before {
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
img{
	border-radius: 20px;
}
</style>
