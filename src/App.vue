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
        this.txtVal = '' //入力後、文字列を空にする
        this.saveToLocalStorage();
        // this.$nextTick(function () { //前の処理が終わってから実行
        //   this.emitScrollToBottom();
        // });
    },
    addArrayYou(){ // ボットのメッセージを追加
      let chatYou = {
        sender: false,
        txt: '',
      };
      this.chats.push(chatYou); //配列にボットのメッセージを入れる
      this.saveToLocalStorage();
      console.log('ボット');
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
      }
    },
    emitScrollToBottom() {
      // this.$nextTick(() => {// ビュー全体がレンダリングされた後にのみ実行されるコード
      this.$refs.contents.scrollToBottom()
      console.log('スクロール下メソッド！！！')
        // });
    },
    reRenderHTML(){
      // debugger; // eslint-disable-line no-debugger
      // this.chats.innerHTML = '';
      this.addArrayMe();
      this.$nextTick(this.emitScrollToBottom);
      setTimeout( ()=>{
      this.addArrayYou();
      this.$nextTick(this.emitScrollToBottom);
      }, 2000); //2秒後に実行
    }
  },
  mounted() { //ライフサイクルフック
    window.onload = ()=>{
      this.loadFromLocalStorage();
      this.$nextTick(this.emitScrollToBottom);
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
