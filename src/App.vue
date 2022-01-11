<template>
  <div class="chatbot">
  <!--親コンポーネント：v-bind:props名="state名"でUserListに値を渡す -->
  <!--     v-model:txtVal="txtVal" -->
    <MessageList
    :chats="chats"
    :player="player"
    :txtVal="txtVal"
    />
  <!--親コンポーネント：v-on:イベント名で値を受け取る -->
    <EntryParts
    v-model:txtVal="txtVal"
    @addBtnParts="addArrayMe"
    />
  <!-- <div v-for="alt in altArray" :key="alt">
  <p>{{alt.me}}</p>
  <p>{{src.imgMe}}</p>
  </div> -->
  </div>
</template>

<script>
import MessageList from './components/MessageList.vue'
import EntryParts from './components/EntryParts.vue'

export default {
  name: 'App',
  data:()=>({ //dataだけは、アロー関数で記述できます
    chats:[],
    txtVal: '',
    player: true,
    // srcArray:[
    //   {imgMe:require('./assets/me.jpg')},
    //   {imgYou:require('@/assets/you.jpg')},
    // ],
    // altArray:[
    //   {me:'自分の画像'},
    //   {you:'相手の画像'},
    // ],
  }),
  components:{
    EntryParts,
    MessageList
  },
  methods:{
    addArrayMe:function(){
      let chatMe = { player: this.player, txt: this.txtVal };
      this.chats.push(chatMe); //配列にユーザーのメッセージを入れる
      this.txtVal = '' //入力後、文字列を空にする
      console.log(this.chats);
    },
    addArrayYou:function(){
      let chatYou = { player: this.player, txt: '今はテキストを挿入します' };
      this.chats.push(chatYou); //配列にボットのメッセージを入れる
      console.log(this.chats);
    },
		// isAlt:function(){
		// 	return this.player ? alt.me: alt.you;
		// },
    // reRenderHTML(){
    //   this.message.innerHTML = '';
    //   this.message.appendChild('a');
    // }
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
