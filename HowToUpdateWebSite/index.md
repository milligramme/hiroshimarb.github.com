l---
layout: page
title: "hiroshima.rbのサイトを更新しよう"
date: 2012-05-27 18:17
comments: true
sharing: true
footer: true
---

このサイトは [Octopress](http://octopress.org/) を使用して作成されています。
hiroshima.rb のメンバーが本サイトを誰でも更新できるように更新方法を記録しています。Octopress を利用する際にも参考になるかも?みんなでどんどんRubyのTipsを増やしていきましょう。

利用には ruby 1.9.2 以降が必要になります。rbenvを利用したインストールがおすすめです。

# リポジトリの取得

更新するためにはまず github からデータを取得する必要があります。
作業をするディレクトリで以下のようにします。

{% codeblock lang:bash %}
git clone git@github.com:hiroshimarb/hiroshimarb.github.com.git
cd hiroshimarb.github.com
{% endcodeblock %}

# ページの作成しよう

ページを作成するには所定の位置にファイルを作成するだけですが、`rake`コマンドを利用してコードジェネレートできます。現状では日本語にしないほうがよさそうです。

{% codeblock lang:bash %}
orake new_page[ページ名]
{% endcodeblock %}

zshを使用している場合、うまく動いてくれません。クオートしましょう。

{% codeblock lang:bash %}
rake "new_page[ページ名]"
{% endcodeblock %}

実行をすると
`source/ページ名/index.md` が作成されます。

# ページの記述形式

生成されたファイルには`---`に囲まれた部分にページの情報を記述されています。
ふたつめの`---`の以降にページの内容を記述していきます。この時の形式はファイルの拡張子によって決まり、デフォルトでは[markdown](http://daringfireball.net/projects/markdown/)となっています。

- TODO Markdown以外の形式は何が使えるのかは把握してないので調べる

# プレビューしてみよう

ページを作成したら、どのように表示されるかプレビューしてみましょう。
以下のコマンドでサーバを立ち上げることができます。

{% codeblock lang:bash %}
rake preview
{% endcodeblock %}

サーバはポート 4000 で起動します。[http://localhost:4000](http://localhost:4000)にアクセスしてみましょう。

# ページを公開しよう

ページを作成したら、インターネットに接続している誰もが閲覧できるように公開しましょう。
まずは公開先の設定をしましょう。

{% codeblock %}
rake 'setup_github_pages[git@github.com:hiroshimarb/hiroshimarb.github.com.git]'
{% endcodeblock %}
これは一度だけ行えば大丈夫です。

公開には、以下のコマンドを使用します。

{% codeblock %}
rake deploy
{% endcodeblock %}
