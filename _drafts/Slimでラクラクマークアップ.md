---
layout: post
category : 元トラック野郎
description: Slimを使ってhtmlを生成する方法を紹介します。
tagline: 
tags : [Slim, html,web]

---
{% include JB/setup %}

webの世界では以前から`html` `css` `javascript`といった技術が使われていてそれは今でも変わらないのですが、最近ではもっと効率的に開発するためにその他の言語からそれらを生成する手法がとられています。  
例えば`css`なら`sass`や`less`から。`javascript`なら`coffeescript`や`typescript`なんかも有名です。`html`だと`Haml`や`Jade`がありますが、今回は`Slim`を使って`html`を生成してみます。

##Slimって？
`Slim`は`ruby`製テンプレートエンジンで、シンプルなマークアップで記述したファイルから`html`を生成することができます。

##Slimをいれる
```
gem install slim
```

##さっそく生成してみる

適当な作業ディレクトリを作成して、`sample.slim`ファイルを次の内容で作成します。

```
doctype html
html
  head
    title Title!!
  body
    h1 This is H1
```

ターミナルで`slimrb`コマンドを入力します

```
slimrb sample.slim
```
こんな`html`が出力されます。

```
<!DOCTYPE html><html><head><title>Title!!</title></head><body><h1>This is H1</h1></body></html>
```

すべて１行で出力されるので見づらい場合は

```
slimrb -p sample.slim 

```

とすると、

```
<!DOCTYPE html>
<html>
  <head>
    <title>Title!!</title>
  </head>
  <body>
    <h1>
      This is H1
    </h1>
  </body>
</html>
```

こんな感じで改行＆インデントされて見やすい`html`が出力されます。  
ファイルに保存したい場合は

```
slimrb sample.slim sample.html
```
これでOKです。

##書き方
###基本
タグ名を書くだけでOK。閉じタグは必要ありません。`<>`もいりません。

```
h1 こんにちは！
p はじめまして
```
これは



    <h1>こんにちは！</h1>
    <p>はじめまして</p>

こんな風になります。

###入れ子
インデントを入れるとタグの入れ子になります。インデントの数は自由です。

```
ul
  li りんご
  li いちご
  li バナナ
```

    <ul>
      <li>りんご</li>
      <li>いちご</li>
      <li>バナナ</li>
    </ul>
    
###テキスト
1行で書く

```
p これは内容です

```

複数行で書く

```
p
  |これは内容です
```

###属性
属性は書き方が色々あります。どれかに統一したほうがいいでしょう。

```
/囲まない
a href="http://www.mosa-architect.com" target="_blank"
  |MOSAアーキテクト

/[]カッコで属性を囲む
a [href="http://www.mosa-architect.com" target="_blank"]
  |MOSAアーキテクト

/()カッコで属性を囲む
a (href="http://www.mosa-architect.com" target="_blank")
  |MOSAアーキテクト
  
```

    <a href="http://www.mosa-architect.com" target="_blank">MOSAアーキテクト</a>
    
ちなみに私は`[]`で統一しています。

###id classをつける
`css`の記法で書くことができます。タグ名を省略するとデフォルトで`div`タグになります。これは便利です。

```
div#user-id.user

/divは省略可能

#user-id.user

```


    <div id="user-id" class="user"></div>


##おまけ
###あれ？この記法あってるのかな？というとき

```
echo "p hello!" |slimrb -s

```
とすると簡単に確認できます。不正な記法のときはエラーになります。

    <p>hello!</p>

ちなみに複数行のときは`echo`コマンドの`-e`オプションを使用します。

```
echo -e "p\n  |this is content"|slimrb -s
```

###既存のhtmlをSlim化したい
`html`を`Slim`化してくれる[html2slim](https://github.com/slim-template/html2slim)というgemがあります。

```
gem install html2slim

html2slim -h
Usage: html2slim INPUT_FILENAME_OR_DIRECTORY [OUTPUT_FILENAME_OR_DIRECTORY] [options]
```



##まとめ
`Slim`を使うとものすごくシンプルに書けますね。記法もとても簡単なのですぐにでも使ってみたくなったのではないでしょうか？

[MOSAアーキテクト](http://www.mosa-architect.com)では会社のホームページを社員が構築・運用していますが、もちろん`Slim`で書いて`html`を生成しています。  
`Slim`には`ruby`コードが書けたりファイルをインクルードする機能があったりするのですが、それはまた別の記事で紹介したいと思います。

