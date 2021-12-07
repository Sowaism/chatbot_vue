<template>
	<div class="entry_input">
		<EntryInput/>
		<Button/>
	</div>
</template>

<script>
import EntryInput from '../components/EntryInput.vue'
import Button from '../components/Button.vue'

export default {
  name: 'EntryParts',
  props: {
    // msg: String
  },
  components:{
	Button,
	EntryInput
  }
}
</script>

<style scoped>
/*menu*/
.entry_input{
	display: flex;
	width: 100%;
	z-index: 4;
}

.entry_input input{
	-webkit-appearance: none;
	-moz-appearance: none;
	appearance: none;
	border-top: none;
	border-left: 1px solid #CFD4D9;
	border-right: 1px solid #CFD4D9;
	border-bottom: none;
	width: 100%;
	font-size: 12px;
	outline: none;
	padding: 11px 4px;
}
</style>
