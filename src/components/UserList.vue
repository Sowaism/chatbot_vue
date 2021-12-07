<template>
	<div id="message_area" class="message_area">
		<ul>
		</ul>
	</div>
</template>

<script>
export default {
  name: 'UserList',
  props: {
    // msg: String
  }
}
</script>

<style scoped>
ul{
	margin: 0 auto;
	padding: 0;
	width:300px;
}
li{
	list-style: none;
}
#message_area {
	height: calc(100vh - 36px);
	overflow: scroll;
}
.my_message,
.you_message {
	display: flex;
	margin:0 4px;
}
.my_message p,
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
.you_message{
	display: flex;
	justify-content:flex-start;
	align-items: center;
}
.my_message{
	display: flex;
	justify-content:flex-end;
	align-items: center;
}
.my_message img,.you_message img{
	border-radius: 20px;
}
</style>
