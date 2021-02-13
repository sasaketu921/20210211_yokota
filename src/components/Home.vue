<!--郵便番号データを検索する郵便番号検索APIを利用して郵便番号を検索すると住所を表示してくれるアプリケーションを作成しましょう。

以下のサイトが例になります。

1500001のような7桁のような番号を入力してみてください。

https://stoic-blackwell-b9013b.netlify.app/

ヒント
inputに入力した情報はv-modelで取得します
ボタンを押した時の処理なので今回はmethodsを使用します
methods内の関数ではaxiosを使用してAPIを叩く処理を記述します。
リファレンスではCURLという特別な書き方で記述されていますが、そちらは参照しないでください
APIのURLは「エンドポイント/postcodes/パスパラメータ?クエリパラメータ」です
取得したデータの取り出し方はこちらを参照ください-->

<template>
  <div id="app">
    <input type="text" v-model="zipcode" maxlength="7"> 
    <button @click="userClick">住所自動検索</button>
    <p>Address:{{ this.addressData }}</p>

  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: "",
      addressData: ""
    };
  },
  methods: {
    async userClick() {
      let url = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipcode}?apiKey=bcBz0exPzK9QSTju4dlLbzeCq1JGtVB8dYvvLEz`);
      // console.log(url);
      this.addressData = url.data[0].allAddress;
      // console.log(this.addressData);
    },
    
  },
};
</script>



