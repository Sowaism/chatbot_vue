<template>
	<div>
		<img src="../assets/me.jpg" width="40" height="40" alt="自分の画像">
	</div>
</template>

<script>
export default {
  name: 'UserMeImg',
  props: {
    // msg: String
  }
}
</script>

<style scoped>
img{
	border-radius: 20px;
}
</style>
