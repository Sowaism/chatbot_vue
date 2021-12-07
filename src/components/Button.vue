<template>
	<button id="addbtn" class="inquiry-next-btn" disabled>送信</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    // msg: String
  }
}
</script>

<style scoped>
#addbtn{
	background-color: #001d47;
	color: #fff;
	border: none;
	cursor: pointer;
	outline: none;
	padding: 0;
	appearance: none;
	width: 48px;
}

#addbtn:disabled{
	background-color: #65717e;
}
</style>
