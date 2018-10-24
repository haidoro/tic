# React公式サイトチュートリアルメモ no4
## BoardにhandleClickを追加とImmutability
stateをコピーにではなくsetState()を使いながらも、直接書き換えてみました。
アプリ自体は正常に作動するも、ESLintは「do not mutate state directly. use setstate(). (react/no-direct-mutation-state)」と警告を出しました。
