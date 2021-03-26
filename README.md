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

***
## Firebase環境構築
***

続いてFirebaseの環境構築に移ります。  

## プロジェクトの作成
***

アカウントを登録し準備ができたら、プロジェクトを作り始めます。
1. `プロジェクトを追加`をクリック
2. プロジェクト名を入力
3. Googleアナリティクスを有効にし、`続行`をクリック
4. Google アナリティクス アカウントを選択または作成し、`プロジェクトを作成`をクリック
5. 新しいプロジェクトの準備ができましたと表示されるのでそのまま`続行`をクリック
   
プロジェクトの作成は以上になります。

## アプリにFirebaseを追加する
***
続いて先程のプロジェクト作成の延長線上で、アプリにFireBaseを入れていきます。  
1. WEBアプリを示す`</>`をクリック
2. アプリのニックネームを入力し、Hostingにチェックを入れ、`アプリを登録`をクリック
3. 「Firebase SDK の追加」は確認のみで`次`へをクリック
4. 「Firebase CLI のインストール」も同様に確認のみで`次`へをクリック
5. Firebase Hosting へのデプロイも同様に確認をし、`コンソールに進む`をクリック
   
アプリにFirebaseを追加する作業は以上になります。

## Firebase CLIをインストールする
***

Firebaseを利用するために、Firebase CLIをインストールします。
```
$ npm install -g firebase-tools
```
最後にFirebaseにログインします。
```
firebase login
```
先に登録していたGooogleアカウントによってログインできたかと思います。
Firebase CLIのインストールは以上になります。

## Firebaseのデプロイをする
***

まずはFirebaseのコンソール画面で初期設定をします。
1. 左のタブから「Realtime Database」を選択
2. `データベースの作成`をクリック
3. ロケーションを選択し`次へ`をクリック
4. 今回は「テストモード」を選択し、`有効にする`をクリック
5. ターミナルに移動しコマンドを入力します
 ```
$ firebase init
 ```
上記コマンドを入力すると初期設定が始まります。
```
? Which Firebase CLI features do you want to set up for this folder? Press Space to select features, then Enter to confirm your choices. 
 ◯ Database: Deploy Firebase Realtime Database Rules
 ◉ Firestore: Deploy rules and create indexes for Firestore
 ◯ Functions: Configure and deploy Cloud Functions
 ◉ Hosting: Configure and deploy Firebase Hosting sites
 ◯ Storage: Deploy Cloud Storage security rules
 ◯ Emulators: Set up local emulators for Firebase features
```
今回使用するプロジェクト(今回はDatabaseを使用)をspaceキーを使って選択し、enterで次に進みます。

```
? Please select an option: (Use arrow keys)
❯ Use an existing project 
  Create a new project 
  Add Firebase to an existing Google Cloud Platform project 
  Don't set up a default project 
? Select a default Firebase project for this directory: (Use arrow keys)
❯ ngchat-xxxx (NgChat) 
```
利用するFirebaseのプロジェクトを確認されるので、上記で作成したプロジェクトを選択します。  
その他にも色々と聞かれますが、上記以外は基本デフォルトの設定で今回は問題なさそうでしたので、流します。  

最後にデプロイをしましょう。
```
$ firebase deploy
```

Hosting URLが表示されると思うのでアクセスして確認します。  
以上でFirebaseの環境構築は完了です。

