# React公式サイトチュートリアルメモ no2
## インタラクティブなコンポーネント
クリックした時にSquareに "X" が入るようにします。
Squareコンポーネントにある buttonタグにonClick属性を記述します。値に入るのはJavaScriptの関数ですからここは{}で囲みます。
`onClick={() => this.setState({value: 'X'})}`のようにアロー関数で記述します。

setStateは単なるsetterメソッドではなく、最終的に再レンダリングまでやっているReactの重要な役割を担っています。

これでマス目をクリックしたらxが表示されるようになります。