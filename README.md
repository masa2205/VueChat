# *Vue.jsとFirebaseを使ったチャットサービスを作る*

 目的はVue.jsとFirebaseについての学習となります。
 エディタは`vs-code`を使用しています。
 <br>

 ## Vue.jsの環境構築
***  
<br>
 前回、「Vue.jsを使用したToDoList」では、HTMLファイル内に公式のドキュメントからCDNを
 引っ張ってきたのですが、今回はCDNを使わず`vue-cli`を使い、Vue.jsの環境構築から始めたいと思います。  
 早速下記に手順を記述しますが、`node`がインストールされている事を前提で進めます。
<br>

## Vue.jsのインストール
***
```
$ npm install -g vue-cli
```
バージョンを確認してインストールが成功したか確認して下さい。
```
$ vue -V
@vue/cli 4.5.12
```
インストールがうまくいきましたら次のコマンドを実行して下さい。
```
$ vue init webpack test-vue
```
上記コマンドを実行すると、様々な設定を入力することになります。
```
? Project name test-vue
? Project descripution A Vue.js project
? Author ユーザー名<ユーザーアドレス>
? Vue build standalone
? Install vue-router? Yes
? Use ESlint to lint your code? No
? Set up unit teste Yes
? Setup e2e tests with Nightwatch? Yes
```
最初に聞かれる設定はディレクトリ名となりますので任意の名前を渡してあげて下さい。  
その他、`Author`以外は基本Enterで流してしまって大丈夫そうですが、今回`ESlint`の設定で後程躓いたので、ここだけNoとしておきました。(エラーに関しては該当箇所で記述致します。)  
設定が終わると共に様々なファイルが`test-vue`ディレクトリ内に生成されたかと思います。  
最後に
```
$ cd test-vue
$ npm run dev
```
を実行して下さいと出るので、こちらを実行させましょう。  
最後に`localhost:8080`にブラウザからアクセスし、Vue.jsの画面が表示されれば環境構築は終了となります。