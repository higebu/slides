class: center,middle
# Go Training

@higebu

---

## アジェンダ

1. Goについて
2. 参考
3. 準備
4. A Tour of Go
5. テストの書き方
6. 標準パッケージいろいろ
7. 課題

---

## Goについて

* 2009年に公開され、2012年にバージョン1になり、最新版は2016/2/17にリリースされた1.6です
* GoogleのRobert Griesemer、Rob Pike、Ken Thompsonの3人が設計した言語です
* 1.5からCではなく、Goとアセンブラで書かれています [No more C](https://golang.org/doc/go1.5#c)
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

* Web
    * [https://golang.org/](https://golang.org/) 公式ページ
    * [https://github.com/golang/go](https://github.com/golang/go) ソース
    * [The Go Playground](https://play.golang.org) ブラウザ上でGolangのコードを実行できます
    * [A Tour of Go](https://tour.golang.org/welcome/1) 後でやる
    * [Effective Go](https://golang.org/doc/effective_go.html) どう書くのが良いんだっけという時に見る
    * [The Go Blog](http://blog.golang.org/) 最新情報とTips
    * [はじめてのGo―シンプルな言語仕様，型システム，並行処理](http://gihyo.jp/dev/feature/01/go_4beginners) ちょっと古いけど日本語だとこれが良さそう
* 本
    * [The Go Programming Language](http://www.gopl.io/) 現状一番良い本で6月に日本語版出るらしい
* Twitter
    * [https://twitter.com/higebu/lists/golang](https://twitter.com/higebu/lists/golang/members)

---

# 準備

## インストール

* [公式ドキュメント](https://golang.org/doc/install)に従って入れれば良い
* 実際の研修ではいろいろインストール済のVMが配られるはず

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

# A Tour of Go

[A Tour of Go](https://tour.golang.org/welcome/1)

---

# テストの書き方

---

# 標準パッケージいろいろ

---

# 課題
