# HTTPでやりとりする仕組み
クライアント側がHTTPリクエストをしてwebサーバー側がHTTPレスポンスを返す
<!-- Markdown記法のヒント

コード記法（1行の中に埋めたい場合）

`code`

コードブロック記法（複数行）

```
print('a')
print('b')
```

-->

## 実習でやったこと (Y)
terminalで

```
$ openssl s_client -crlf -connect www.kobedenshi.ac.jp:443
  GET / HTTP/1.0
```

を実行してHTTPレスポンスを見てから

```
$ script kd.txt
```

でHTTPレスポンスを出力する

```
$ git add .
$ git commit -m '6/7 課題提出'
$ git push -u origin master
```

kd.txtとREADME.mdを提出
## 自分で調べたこと
[神戸電子のサイト](https://www.kobedenshi.ac.jp/)にアクセスするとublockoriginにhttps://b92.yahoo.co.jp/js/s_retargeting.jsがブロックされていたので
b92yahooとは何か調べてみた

https://promotionalads.yahoo.co.jp/service/ydn/
> Yahoo!ディスプレイアドネットワーク(YDN)とは
> アプローチしたいターゲットの属性」や「過去にウェブサイトを訪れた人」などの条件を設定し、
> それぞれの条件に一致するインターネットユーザーが閲覧しているYahoo! JAPANや提携サイトに広告を表示します。

[SSL3.0の脆弱性について](https://www.acunetix.com/blog/articles/tls-vulnerabilities-attacks-final-part/)
## HTTPメッセージ (kd.txt) のうち、最も重要だと思う部分を貼り付けてください

```kd.txt
GET / HTTP/1.0

HTTP/1.0 200 OK

ontent-Type: text/html; charset=UTF-8
```

## それはなぜですか？
リクエスト行とステータスコードと言語の情報があるこの三行が重要だと感じました

## わかったこと・気づいたこと
- サーバーはApacheを使っている
- ステータスコードは200 OK
- SSL3.0を使っているので脆弱性がある
- ソースコードを見ると
    - google analyticsを使っている
    - 前のバージョンのコードらしきものがコメント化されて残っている
    - IE 9 のためのjsファイルがコメント化されて残っている