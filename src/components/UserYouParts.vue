<template>
  <li>
    <div class="you_message">
		<UserYouImg/>
		<UserYouTxt/>
	</div>
  </li>
</template>

<script>
import UserYouImg from '../components/UserYouImg.vue'
import UserYouTxt from '../components/UserYouTxt.vue'

export default {
  name: 'UserYouParts',
  props: {
    // msg: String
  },
  components:{
	UserYouImg,
	UserYouTxt
  }
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
</style>
