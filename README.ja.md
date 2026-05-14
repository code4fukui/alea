# Alea

Johannes Baagøe氏によるAlea PRNGの、コピー＆ペーストで使えるシンプルな実装です。

## 機能
- JavaScript組み込みの`Math.random()`よりも現代的で高性能な疑似乱数生成器（PRNG）を提供します。
- `importState`および`exportState`メソッドを通じて、2つのAlea PRNGの状態を同期可能です。

## インストール
```bash
npm install alea
```
または
```js
import Alea from 'https://code4fukui.github.io/alea/alea.js'
```

## 使い方
```js
import Alea from 'alea'

const prng = new Alea() // オプションでシード値のパラメータを追加可能

const nextRandnum = prng() // Aleaの戻り値を呼び出すだけ
```

## 同期
```js
const prng1 = new Alea(200)

prng1()
prng1()

// いくつか乱数を生成した後、新しいPRNGを初期化します

const prng2 = Alea.importState(prng1.exportState())

// これは true, true, true と出力されるはずです
console.log(prng2() == prng1())
console.log(prng2() == prng1())
console.log(prng2() == prng1())
```

同期機能により、クライアントはサーバー上で実行されているシミュレーション（例: ゲーム）に参加し、毎回の更新を完全にサーバーに依存することなく、ローカルのシミュレーションをサーバーと完全に同期させることができます。

## ライセンス
MIT License — [LICENSE](LICENSE)を参照してください。
