<template>
	<li>
		<div class="my_message">
			<UserMeTxt/>
			<UserMeImg/>
		</div>
	</li>
</template>

<script>
import UserMeImg from '../components/UserMeImg.vue'
import UserMeTxt from '../components/UserMeTxt.vue'

export default {
  name: 'UserMeParts',
  props: {
    // msg: String
  },
  components:{
	UserMeImg,
	UserMeTxt
  },
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
</style>
