<!--親コンポーネント：v-bind:props名="state名"でMessageListに値を渡す -->
<!--親コンポーネント：v-on:イベント名で値を受け取る -->
<template>
  <div class="chatbot">
    <MessageList
      :chats="chats"
      :txtVal="txtVal"
      ref="contents"
      @emitScrollToBottom="scrollToBottom()"
    />
    <EntryParts
      v-model:txtVal="txtVal"
      @addBtnParts="reRenderHTML()"
    />
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
        this.txtVal = '' //入力後、文字列を空にする
        console.log(this.chats);
        this.saveToLocalStorage();
    },
    addArrayYou(){ // ボットのメッセージを追加
      let chatYou = {
        sender: false,
        txt: 'jjjj',
      };
      this.chats.push(chatYou); //配列にボットのメッセージを入れる
      console.log(this.chats);
      this.saveToLocalStorage();
    },
    // scrollToBottom(){
    //   const dom  = this.$refs.contents[0]; //タグを参照
    //   const rect = dom.clientHeight; //要素の高さを取得
    //   dom.scrollTo(0, rect);
    //   console.log(rect);
    //   console.log(dom);
    //   console.log(dom.scrollTo(0, rect));
    // },
    saveToLocalStorage() {
      const jsonObj = JSON.stringify(this.chats);
      localStorage.setItem('chats', jsonObj);
    },
    loadFromLocalStorage() {
        const chatsObj = localStorage.getItem('chats');
        const jsObj = JSON.parse(chatsObj);
        console.log(jsObj);
      if (jsObj) { //jsObj !== null
        console.log('ローカルストレージ保存したものを出力');
        this.chats = jsObj;
        this.reRenderHTML();
      }
    },
    emitScrollToBottom() {
      console.log('テスト')
      console.log(this.$refs.contents)
      console.log(this.$refs.contents.scrollToBottom)
      this.$refs.contents.scrollToBottom
    },
    reRenderHTML(){
      this.addArrayMe();
      setTimeout(() => {this.addArrayYou();}, 2000); //2秒後に実行
      this.emitScrollToBottom()
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
