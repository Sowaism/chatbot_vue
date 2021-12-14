<template>
	<div class="chatbot">
		<UserList/>
		<EntryParts/>
	</div>
</template>

<script>
import UserList from '../components/UserList.vue'
import EntryParts from '../components/EntryParts.vue'

export default {
  name: 'Home',
	data:function() {
		return{
			chats : [],
		}
	},
  components:{
	EntryParts,
	UserList
  },
}
</script>

<style scoped>
.chatbot{
	position: relative;
	border-radius: 4px;
	border:1px solid #888;
	height: 100%;
	margin: 0 auto;
	background-color: #547FBC;
}
</style>
