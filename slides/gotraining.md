class: center,middle
# Go Training

@higebu

---

## アジェンダ

1. Goについて
2. 参考
3. 準備
4. A Tour of Go
5. 補足
6. テストの書き方
7. 標準パッケージいろいろ
8. 課題

---

## Goについて

* 2009年に公開され、2012年にバージョン1になり、最新版は2016/2/17にリリースされた1.6
* GoogleのRobert Griesemer、Rob Pike、Ken Thompsonの3人が設計した言語
* 1.5からCではなく、Goとアセンブラで書かれている
    * [No more C](https://golang.org/doc/go1.5#c)
* 特徴
    * 静的型付け言語
    * コンパイル言語なのでデプロイしたり、コンテナに入れたりしやすい
    * クロスコンパイルも可能
    * 標準ライブラリがわりと豊富
    * 並行処理に強い
    * GCある
    * `go fmt`などの公式ツールが強力

---

# 参考

## Web

* [https://golang.org/](https://golang.org/) 公式ページ
* [https://github.com/golang/go](https://github.com/golang/go) ソース
* [The Go Playground](https://play.golang.org) ブラウザ上でGolangのコードを実行できる
* [A Tour of Go](https://tour.golang.org/welcome/1) 後でやる
* [Effective Go](https://golang.org/doc/effective_go.html) どう書くのが良いんだっけという時に見る
* [Go open source projects](https://github.com/golang/go/wiki/Projects) 全部ではないけどGoでできたOSSが並んでいる
* [GitHub Trending in Go](https://github.com/trending/go)
* [The Go Blog](http://blog.golang.org/) 最新情報とTips
* [はじめてのGo―シンプルな言語仕様，型システム，並行処理](http://gihyo.jp/dev/feature/01/go_4beginners) ちょっと古いけど日本語だとこれが良さそう

---

# 参考

## 本

* [The Go Programming Language](http://www.gopl.io/)
    * 6月に日本語版出るらしい

## Twitter

* [https://twitter.com/higebu/lists/golang](https://twitter.com/higebu/lists/golang/members)
    * Goのすごそうな人を入れてあります

## GitHub Awards

* [Top Go GitHub developers worldwide](http://github-awards.com/users?language=go)
* [Top Go GitHub developers in Japan](http://github-awards.com/users?country=japan&language=go)

---

# 準備

## インストール

* [公式ドキュメント](https://golang.org/doc/install)に従って入れれば良い
* 実際の研修ではいろいろインストール済のVMが配られるはず
* `go`コマンドを実行できるか、`echo $GOPATH`が表示されるか確認してください

---

# 準備

## エディタ

* Vimだったら[vim-go](https://github.com/fatih/vim-go)入れておくと良いです
* 他のエディタについては知りませんがググればいろいろ出てくると思います
* とにかく保存時に[goimports](https://godoc.org/golang.org/x/tools/cmd/goimports)とか[golint](https://github.com/golang/lint)とかでチェックするようにしておくと捗ります

---

# 準備

## Hello, World!

まず、`go get`します

```sh
go get github.com/higebu/gotraining
cd $GOPATH/src/github.com/higebu/gotraining/helloworld/
```

エラーになったらエラーメッセージをよく読んで対処してください

---

# 準備

## Hello, World!

* [Playground](http://play.golang.org/p/992fMmkkxr)

`go run` で実行できる

```sh
go run helloworld.go
```

`Hello, World!` と表示されるはず

`go build` でコンパイルできる

```sh
go build helloworld.go
./helloworld
```

`Hello, World!` と表示されるはず

---

# 準備

## Hello, World!

`go install`すると`$GOPATH/bin`配下にバイナリができます

```
go install github.com/higebu/gotraining/helloworld
$GOPATH/bin/helloworld
```

`Hello, World!` と表示されるはず

---

# A Tour of Go

事前課題として出していた[A Tour of Go](https://tour.golang.org/welcome/1)ですが、やっていない人もいると思うのでやりましょう

わからないことがあったら周りにいる先輩に聞いてください

たぶん、午前中いっぱいくらい

Exerciseは飛ばしてざーっと読む感じで良いです

余裕があったらExerciseをやってもいいし、課題を先にやっていてもいいです

---

# 補足

A Tour of Goで説明されていないけど知っておいた方がいいことなどを補足します

---

# 補足

## iota

constで定義した定数に連番を付けられます

```golang
const (
    a = iota
    b
    c
)
```

例1: [Playground](https://play.golang.org/p/lPT7Lflgmw)
例2: [Playground](https://play.golang.org/p/dIsrapo5AV)

ローカルで動かしたい場合

```
cd $GOPATH/src/github.com/higebu/gotraining/iota
```

---

# 補足

## syncパッケージ

---

# テストの書き方

テストには[testing](https://golang.org/pkg/testing/)パッケージを使う

```
cd $GOPATH/src/github.com/higebu/gotraining/hello
```

[![GoDoc](https://godoc.org/github.com/higebu/gotraining/hello?status.svg)](https://godoc.org/github.com/higebu/gotraining/hello)

* テストの実行
    ```
    go test -v
    ```

* ベンチマーク
    ```
    go test -bench .
    ```

---

# 標準パッケージいろいろ

公式ドキュメント見ながらサンプルを紹介していく感じ

---

# 課題

何か課題をやる
