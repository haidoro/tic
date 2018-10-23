# React公式サイトチュートリアルメモ

作成するもの
tic-tac-toe game ○×ゲームのこと

## 環境設定
公式サイトでは　code penを使っているが、自前で行います。

create-react-appを導入してReactの環境設定を行います。
面倒な設定など必要ありませんので、気軽にReact本来の組み立てに集中することができます。
 
今回の手順はMacでおこなったものです。
* Node.jsがインストールされている必要があります。
* yarnがインストールされている必要があります。

## create-react-app導入
create-react-appを以下コマンドでグローバルでインストールします。
```
yarn global add create-react-app
```

## test作成
以下のコマンドを実行するとHomeの中にtestフォルダが作成されてcreate-react-app環境が構築されます。
```
create-react-app test
```
testフォルダに移動します。
```
cd test
```
サーバーを稼働させます。
```
yarn start
```
サーバー停止はctrl+C

* ここでエラーが出ました。以前学習した内容は問題なかったのですが、
原因はwebpackのバージョンがグローバルのものと今回導入したローカル環境のもので違っているのが原因でした。グローバルのバージョンをローカルのものに合わせて無事エラーは解決。

## 3つのコンポーネント作成
次の3つのコンポーネントを作成。どれもclassでコンポーネントを定義します。イベントの設定はありませんのでこの章ではマス目に0から8までの数字が表示されてお終いです。

* Square
* Board
* Game

### Squareコンポーネント
Squareコンポーネントはボタンを作成しています。
Class型コンポーネントは「render」 メソッドを定義する決まりになっています。このメソッドが、コンポーネントが呼び出された際に「render」する内容となります。

ここでは、returnでbuttonタグを返すだけの内容になっています。
さて、ここでbuttonタグがHTML文のようにそのまま記述されています。
このファイルはあくまでJavaScriptファイルですからJavaScriptの記法に従わないといけません。
それではなぜHTMLタグがそのまま使えるのでしょうか？
答えはJSXの記法に従っているからです。

JSXの記述のベースはjavascriptの世界です。
けれどもタグはクオテーションを使わずに直接記述できます。
しかもタグは好きな名前のものを作れます。これがJSXの仕組みです。
ただし、タグは一つだけ記述できますので、複数のタグを使いたい場合は親タグの中に入れ子にします。
タグの中の世界はもうHTMLの世界です。このタグのことをreactElementと呼びます。
そして逆にタグの中でJavaScriptを使いたい場合は、{}で囲んで使います。これはあくまでタグの中でのことだよ。

ポイント：Squareコンポーネントのrenderメソッドの中の記述はJSXの記法になっていることです。

次に、ボタンの表示内容は {this.props.value} となります。
{this.props.value}の使い方がここでのポイントになります。

propsは別のコンポーネントに値やコールバック関数を渡すことができます。

Reactにおける値の渡し方はpropsを介して渡す仕組みになっています。
今回の例ではBoardからSquareへデータを渡しています。


### Boardコンポーネント
現段階ではBoardコンポーネントが中心の母体の役割をします。

このコンポーネントでは `renderSquare(i){return <Square value={i} />;}`を定義しています。

定義したrenderSquare関数は自身のrender()内で実行しています。
render()は引数として記述したタグを書き出すためのものです。
この中でrenderSquare関数を実行しています。引数はそれぞれ0から8までの整数が与えられています。
renderSquare関数が実行されるとpropsを通じてSquareコンポーネントに値が渡されてボタンタグの中に0から8までの数値が表示されることになります。

表示結果は以下のようになります。
```
<div id="root">
<div class="game">
<div class="game-board">
<div>
<div class="status"> Next player: X </div> 
<div class="board-row"> <button class="square"> 0 </button> <button class="square"> 1 </button> <button class="square"> 2 </button> </div>
 <div class="board-row"> <button class="square"> 3 </button> <button class="square"> 4 </button> <button class="square"> 5 </button> </div> 
 <div class="board-row"> <button class="square"> 6 </button> <button class="square"> 7 </button> <button class="square"> 8 </button> </div> 
 </div>
 </div> 
 <div class="game-info"><div>  
 </div> <ol>  </ol> </div> 
 </div></div>
```


### Gameコンポーネント
Gameコンポーネントはここでは何もしていません。
ただBoardコンポーネントを呼び出して、 ReactDOM.render()に渡しているだけです。
Gameコンポーネントは以降の章で活用するものです。
