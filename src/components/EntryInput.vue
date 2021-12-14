<template>
	<input id="txtEntry" type="text" class="inquiry-key-entry" placeholder="メッセージを入力" :value="txtVal.value">
</template>

<script>
export default {
  name: 'EntryInput',
  props: {
    txtVal:{
    type:String,
    value:'',
    }
  },
  methods:{
    // 		enterButtonFlag:function() {
    //     if (txtVal() == false) {
    //         this.addBtn.disabled = true;
    //     } else {
    //         this.addBtn.disabled = false;
    //     }
    //     return;
    // },
  }
}
</script>

<style scoped>
</style>
