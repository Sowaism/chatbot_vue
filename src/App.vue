<template>
  <div class="chatbot">
    <UserList/>
    <EntryParts/>
  </div>
</template>

<script>
import UserList from './components/UserList.vue'
import EntryParts from './components/EntryParts.vue'

export default {
  name: 'App',
  data:()=>({ //dataだけは、アロー関数で記述できます
    chats:[]
  }),
  provide() { //provideは、アロー関数不可
    return {
      chats: this.chats,
    }
},
  components:{
    EntryParts,
    UserList
  },
  methods:{
		addItem:function(){
			// this.chats.innerHTML = '';
			let chatMe ={
				me: {player: true, txt:this.txtVal}
			}
      let chatYou ={
				you: {player: false, txt:this.botTxts}
			}
			this.chats.push(chatMe); //配列にmeのメッセージを入れる
      console.log(this.chats);
			this.txtVal = '' //入力後、文字列を空にする
      this.chats.push(chatYou); //配列にmeのメッセージを入れる

		}
  },
}
</script>

<style>
body {
	color: #333;
	font-family: 'Roboto', sans-serif;
	font-size: 14px;
	margin: 0;
}
.chatbot{
	position: relative;
	border-radius: 4px;
	border:1px solid #888;
	height: 100%;
	margin: 0 auto;
	background-color: #547FBC;
}
</style>
