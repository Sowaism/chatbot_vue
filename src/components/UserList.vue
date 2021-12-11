<template>
	<div id="message_area" class="message_area">
		<ul>
			<UserMeParts/>
			<UserYouParts/>
		</ul>
	</div>
</template>

<script>
import UserMeParts from '../components/UserMeParts.vue'
import UserYouParts from '../components/UserYouParts.vue'

export default {
  name: 'UserList',
  props: {
    // msg: String
  },
  components:{
	UserMeParts,
	UserYouParts
  }
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
</style>
