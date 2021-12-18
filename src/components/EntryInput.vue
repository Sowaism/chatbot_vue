<template>
	<input id="txtEntry" type="text" class="inquiry-key-entry" placeholder="メッセージを入力" :value="txtVal">
</template>

<script>
export default {
  name: 'EntryInput',
  props: {
    txtVal:{
    type:String,
    default:'a',
    }
  },
  methods:{
  }
}
</script>

<style scoped>
</style>
