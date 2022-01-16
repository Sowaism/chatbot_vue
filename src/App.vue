<!--親コンポーネント：v-bind:props名="state名"でMessageListに値を渡す -->
<!--親コンポーネント：v-on:イベント名で値を受け取る -->
<!--      @emitScrollToBottom="scrollToBottom()"-->
<template>
  <div class="chatbot">
    <MessageList
      :chats="chats"
      :txtVal="txtVal"
      ref="contents"
    />
    <EntryParts
      v-model:txtVal="txtVal"
      @addBtnParts="reRenderHTML()"
    />
    <!-- @scrollBtnParts="emitScrollToBottom()" -->
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
  }),
  components:{
    EntryParts,
    MessageList
  },
  methods:{
    addArrayMe(){ // ユーザーのメッセージを追加
      let chatMe = {
        sender: true,
        txt: this.txtVal,
      };
        this.chats.push(chatMe); //配列にユーザーのメッセージを入れる
        this.emitScrollToBottom();
        this.txtVal = '' //入力後、文字列を空にする
        // console.log(this.chats);
        this.saveToLocalStorage();
    },
    addArrayYou(){ // ボットのメッセージを追加
      let chatYou = {
        sender: false,
        txt: 'jjjj',
      };
      this.chats.push(chatYou); //配列にボットのメッセージを入れる
      this.emitScrollToBottom();
      // console.log(this.chats);
      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      const jsonObj = JSON.stringify(this.chats);
      localStorage.setItem('chats', jsonObj);
    },
    loadFromLocalStorage() {
        const chatsObj = localStorage.getItem('chats');
        const jsObj = JSON.parse(chatsObj);
        // console.log(jsObj);
      if (jsObj) { //jsObj !== null
        console.log('ローカルストレージ保存したものを出力');
        this.chats = jsObj;
        this.reRenderHTML();
      }
    },
    emitScrollToBottom() {
      console.log('テスト')
      // console.log(this.$refs.contents)
      // console.log(this.$refs.contents.scrollToBottom)
      this.$refs.contents.scrollToBottom()
    },
    reRenderHTML(){
      this.addArrayMe();
      this.emitScrollToBottom();
      setTimeout(() => {this.addArrayYou();}, 2000); //2秒後に実行
    },
  },
  mounted() { //ライフサイクルフック
    window.onload = ()=>{
      this.loadFromLocalStorage();
  }
}
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
