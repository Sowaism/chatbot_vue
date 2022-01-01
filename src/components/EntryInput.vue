<template>
	<!-- <input id="txtEntry" type="text" class="inquiry-key-entry" placeholder="メッセージを入力" :value="txtVal"> これでもいけます！-->
  <input 
    id="txtEntry"
    type="text"
    class="inquiry-key-entry"
    placeholder="メッセージを入力"
    :value="txtVal"
    @input="$emit('update:txtVal', $event.target.value)"
  >
</template>

<script>
export default {
  name: 'EntryInput',
  props: {
    txtVal:{
    type:String,
    default:'',
    }
  },
  methods:{
  },
  emits:['update:txtVal']
}
</script>

<style scoped>
</style>
