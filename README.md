# React公式サイトチュートリアルメモ no3
## stateを親に渡す
複数の子コンポーネントからデータを集めたり、もしくは二つの子コンポーネント同士に連携させたい時は、stateを上位に移動させて親コンポーネントに保持させます。
そうすれば、親は、propsを介して、stateを子コンポーネント全てに戻すことができ、さらには、子コンポーネントは、子同士そして親と、常に同期することができる。

Boardにコンストラクタを追加して、9つのnullが入った配列を初期stateとして設定します。
記述は次のようにします。
`squares: Array(9).fill(null)`
この9つのnull配列は9つのsquareに対応していることになります。

さらにrenderSquare関数は次のように変更します。

```
renderSquare(i) {
    return <Square value={this.state.squares[i]} />;
  }
```

