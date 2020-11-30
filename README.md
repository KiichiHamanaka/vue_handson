## やっとけ
```
git clone これ
cd 01_handson
yarn install
cd 02_completed
yarn install
```
ポート閉じられてたら動かないのでセキュリティソフトの類とかオフにしてね


# vue_handson

11/13日開催予定
3日前には資料と開発環境完成させる

## はじめに
このハンズオンではVueを使ったことがない よくあるeラーニングや業務で軽くJSとかやった～JQueryしかつかったことね～みたいな人間のためにやります

### このハンズオンで学べること
- Vue.js基礎
- Vue Rooter
- VueX

## このハンズオンでやらないこと
- HTML,CSS,JavaScript文法諸々
- 環境セットアップまわり
- テスト,デプロイ,サーバーサイドとのやりとり
- JQueryに比べて云々や他の仮想DOMライブラリとの比較

## 今日作るもの
Amaz◯nみたいなECサイト
トップ画像 商品+カート画像 決済完了画面画像

## Vue.js基礎


### Vue.jsって？

### はろーわーるど

既存のhtmlに付け加える感じで書くよ～～～


### Vueオブジェクト
データバインディング
data
el
filters
methods
computed

elで指定したDOM要素がマウント対象になる
elプロパティはDOM要素のオブジェクトかCSSセレクタの文字列を指定できます

dataプロパティにはUIの状態となるデータのオブジェクトを指定します

data:{
  キー: 値,
  キー: 値,
  ...
  キー: 値,
}

var items = [{
    name: '鉛筆',
    price: 300,
    quantitiy: 0
}, {
    name: 'ノート',
    price: 400,
    quantitiy: 0
}, {
    name: '消しゴム',
    price: 500,
    quantitiy: 0
}]

data:{
  items:items
}

VueインスタンスのデータをHTMLにテキスト展開するとき

```
//{{}}で囲む
<p>{{ items[0].name }}</p>
```

filters テキストフォーマット処理を適用する仕組み
DateオブジェクトをYYYY/MM/DDとか0.5を50%に
## コンポーネント

## Vue Rooter

## VueX

## おめでとう！

## 他にも

## 謝辞
Evan You
れいや
聞いてくれたおまいら
