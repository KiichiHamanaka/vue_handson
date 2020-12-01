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
コンストラクタオプション
- data
- el
- filters
- methods
- computed

### el(Vueインスタンスのマウント)

elで指定したDOM要素がマウント対象になる
elプロパティはDOM要素のオブジェクトかCSSセレクタの文字列を指定できます

### data(UIのデータ定義)
dataプロパティにはUIの状態となるデータのオブジェクトを指定します

```
data:{
  キー: 値,
  キー: 値,
  ...
  キー: 値,
}
```

```
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
```


#### テンプレート構文

データの変更に応じてビューを更新する仕組みをデータバインディングという

- Mustache記法によるデータの展開 
{{}}で囲む
- ディレクティブによるHTML要素の拡張
標準のHTMLに対して独自の属性を追加したもの v-で名前が始まる属性 後でまた説明します

##### VueインスタンスのデータをHTMLにテキスト展開するとき

```
//{{}}で囲む
<p>{{ items[0].name }}</p>
//js式も書ける
<p>{{ items[0].price * items[0].quantitiy }}</p>
```

##### テキストだけじゃなく属性にも展開出来る
HTMLの属性に対してはMustache記法は使えないのでv-bindディレクティブを使う
v-bind:htmlの属性名="dataの属性値"

```
<button id="b-button" v-bind:title="loggedInButton" v-bind:disabled="!canBuy">購入</button>
var vm = new Vue({
    el: '#b-button',
    data: {
        loggedInButton: '非ログイン時のため、購入できません',
        canBuy: false
    }
})
```

#### filters(フィルタ)
テキストフォーマット処理を適用する仕組み
DateオブジェクトをYYYY/MM/DDとか0.5を50%に

```
filters: {
  フィルタ名: function value(){
  //実行内容
  }
}
```

定義したフィルタは

```
{{ 値|フィルタ名 }}
```

で使える

ちなみにVue3でfilterは使えなくなるので正直覚えなくてもいいです

#### computed(算出プロパティ)
データから派生するデータをプロパティとして公開する仕組み

あれさっきこんなんやらんだ？

```
//js式も書ける
<p>{{ items[0].price * items[0].quantitiy }}</p>
```

でもこれが&&や||でめちゃめちゃ複雑になったら？

Mustache記法で複雑な処理は保守が大変な上に
そもそもテンプレートには記述出来ない式があるよ
複雑な処理は基本的にcomputed内で書きましょう

```
new Vue({ //関数として実装されるが、参照時はプロパティとして機能
  // ...
    computed: {
      算出プロパティ名:function(){
        //hoge
      }
    }
})
```    

テンプレ内で無理にやろうとする感じの

```
<p>{{ items.reduce(function(sum,item){return sum + (item.price*item.quantity),0);}}</p>
```

なげー！わからん！

computedで上を治すと・・・？

```
//ロードされ,Vueがグローバル変数として定義されているか確認
new Vue({
    //マウントやデータ定義
    computed:{
      totalPrice: function () {
        return this.items.reduce(function (sum, item) {
            return sum + (item.price * item.quantitiy)
        }, 0)
      }
    }
})
```

算出プロパティはメソッドじゃないので呼び出す際に()いりませーん


```
totalPriceWithTax: function () {
        return Math.floor(this.totalPrice * 1.1)
}
```

算出プロパティに依存した算出プロパティも定義できるよーん


#### thisは何なの
算出プロパティやメソッドでデータや算出プロパティを参照したいときはthis経由で参照します
thisがサスのはVueインスタンス自身になる

## ディレクティブ
Vue.jsでは標準のHTMLに対して独自の属性を追加することで、属性値の式の変化に応じたDOM操作を行います
この特別な属性のことをディレクティブといいます。 v-から始まる属性名を持つ
ディレクティブの属性値にはJS式を与える

### よく使うであろうディレクティブ
- v-if/v-show
- v-bind 

#### v-if/v-show(条件付きレンダリング)

引数がtrueのときだけ表示する
頻繁に切り替わるやつはshow使え

#### v-bind(属性に値をバインド)
v-bind:classは:classにv-bind:styleは:styleのように省略出来るよ！

#### ComputedとMethodsの違い

## コンポーネント

## Vue Rooter

## VueX

## おめでとう！

## 他にも

## 謝辞
Evan You
れいや
聞いてくれたおまいら
