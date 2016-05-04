class: center,middle
# Go Training

Version 2016

---

## アジェンダ

1. Goについて
2. 参考
3. 準備
4. A Tour of Go
5. 補足
6. テスト
7. 標準パッケージいろいろ
8. Vendoring
9. 課題

---

# Goについて

* 2009年に公開され、2012年にバージョン1になった
* 現時点での最新版は2016/04/20にリリースされた1.6.2
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

# Goについて

## 弊社とGo

* たぶんサービスではほぼ使われていない
    * DRサービスでは一部使っている
    * 他も探したらあるかもしれない
* インフラ方面での利用
    * [Hashicorp](https://www.hashicorp.com/)製品を使ったりいじるときにGoを書いている
    * DockerとかKubernetesとかGoで書かれているものが増え、VMwareも[GoのSDK](https://github.com/vmware/govmomi)とか[Goでできたプロダクト](https://github.com/vmware/vic)を作り始めている

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

* Vimだったら[fatih/vim-go](https://github.com/fatih/vim-go)入れておくと良いです
* Emacsだったら[dominikh/go-mode.el](https://github.com/dominikh/go-mode.el)というのが良いらしいです
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

* `go run` で実行できる
    ```sh
    go run helloworld.go
    ```

    `Hello, World!` と表示されるはず

* `go build` でコンパイルできる
    ```sh
    go build helloworld.go
    ./helloworld
    ```

    `Hello, World!` と表示されるはず

---

# 準備

## Hello, World!

`go install`すると`$GOPATH/bin`配下にバイナリができます

```sh
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

* iota
* 並行処理の補足

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

* 例1: [Playground](https://play.golang.org/p/lPT7Lflgmw)
* 例2: [Playground](https://play.golang.org/p/dIsrapo5AV)
    * ローカルで動かしたい場合
    ```
    cd $GOPATH/src/github.com/higebu/gotraining/iota
    ```

---

# 補足

## 並行処理の補足

[資料](http://hitsumabushi.github.io/slides/?golang-concurrency)

---

# テスト

テストには[testing](https://golang.org/pkg/testing/)パッケージを使う

例は下記のディレクトリにあります

```sh
cd $GOPATH/src/github.com/higebu/gotraining/hello
```

---

# テスト

## テスト実行

`xxx_test.go`にTestXxxを書いておくとテストできる

```sh
go test -v
```

下記のような出力になるはず

```
=== RUN   TestHello
--- PASS: TestHello (0.00s)
=== RUN   ExampleHello
--- PASS: ExampleHello (0.00s)
PASS
ok      github.com/higebu/gotraining/hello      0.003s
```

Exampleを使うとgodocで見られるしテストもできる [![GoDoc](https://godoc.org/github.com/higebu/gotraining/hello?status.svg)](https://godoc.org/github.com/higebu/gotraining/hello)

---

# テスト

## カバレッジ

カバレッジも確認できる

```sh
go test -cover
```

下記のような出力になるはず

```
PASS
coverage: 100.0% of statements
ok      github.com/higebu/gotraining/hello      0.003s
```

---

# テスト

##  ベンチマーク

BenchXxxを書いておいて、`-bench` を付けるとベンチマークできる

```sh
go test -bench .
```

下記のような出力になるはず

```
PASS
BenchmarkHello-4         5000000               345 ns/op
ok      github.com/higebu/gotraining/hello      2.075s
```

`go test --help`してどんなオプションがあるか見ておいてください

---

# 標準パッケージ紹介

* [パッケージ一覧](https://golang.org/pkg/)
* Goを書いていて、〇〇ってGoでどう書くんだっけと思ったらとりあえずここを見に来る
* なさそうと思って自分でパッケージを作ったりしないで探してみる
* 各パッケージ自体もちろんGoで書かれているので書き方の参考にもなる

---

# 標準パッケージ紹介

## [bufio](https://golang.org/pkg/bufio/)

* 名前の通り、bufferd I/Oのパッケージ
* 標準入力から1行ずつ読み込むとか
    ```golang
    scanner := bufio.NewScanner(os.Stdin)
    for scanner.Scan() {
        fmt.Println(scanner.Text())
    }
    if err := scanner.Err(); err != nil {
        fmt.Fprintln(os.Stderr, "reading standard input:", err)
    }
    ```

---

# 標準パッケージ紹介

## [encoding/json](https://golang.org/pkg/encoding/json/)

* jsonのエンコード、デコードをするパッケージ
* encoding配下には他にもいろいろな形式にエンコード、デコードするパッケージがある
* [Marshalの例](https://play.golang.org/p/ZDb6bVGiO6)
* [Unmarshalの例](https://play.golang.org/p/64LCjbg6pI)

---

# 標準パッケージ紹介

## [flag](https://golang.org/pkg/flag/)

* コマンドのフラグをパースするためのパッケージ
    * [例](https://github.com/higebu/gotraining/blob/master/flag-example/main.go)
    * [playground](https://play.golang.org/p/0BHXOKE1-j)

---

# 標準パッケージ紹介

## [html/template](https://golang.org/pkg/html/template/)

* テンプレートからhtmlを生成するためのパッケージ
* [例](https://play.golang.org/p/x7pWBZL2Zl)

---

# 標準パッケージ紹介

## [io](https://golang.org/pkg/io/), [io/ioutil](https://golang.org/pkg/io/ioutil/)

* I/O関連のパッケージ
* io.Copyとかよく使うかもしれない
    * [例](https://play.golang.org/p/PvRHPcT2QF)
* ioutil.ReadAllも便利だけどでかいファイルとか読むとメモリあふれるので注意
    * [例](https://play.golang.org/p/FUgPAZ9w2X)

---

# 標準パッケージ紹介

## [log](https://golang.org/pkg/log/)

* ログのためのパッケージ
* 標準じゃないけど[github.com/Sirupsen/logrus](https://github.com/Sirupsen/logrus)が人気
* 何かライブラリとかツールとか作るときはLoggerは設定したものを渡せるように作っておくと良い

---

# 標準パッケージ紹介

## [os](https://golang.org/pkg/os/), [os/exec](https://golang.org/pkg/os/exec/)

* OS関連のパッケージ
* OSの種類を判別するとかファイル読むとか
    ```golang
    file, err := os.Open("file.go")
    if err != nil {
        log.Fatal(err)
    }
    ```

* os/exec はコマンドを実行するときに使う
    * [例](https://play.golang.org/p/R9V-5MpHyK)

---

# 標準パッケージ紹介

## [path](https://golang.org/pkg/path/)

* path操作するためのパッケージ
* 自分で文字列つなげて間に`/`入れるとかしなくて良い
* urlは[net/url](https://golang.org/pkg/net/url/)

---

# 標準パッケージ紹介

## [strconv](https://golang.org/pkg/strconv/)

* stringと各種データ型の変換をするためのパッケージ
* 何かをstringにしたいとかstringからintにしたいとかで使う
* stringにしたいときは`fmt.Sprintf`を使うという手もあって、特に整形したいときは`fmt.Sprintf`

---

# 標準パッケージ紹介

## [strings](https://golang.org/pkg/strings/)

* stringいじるためのパッケージ
* [公式のExamples](https://golang.org/pkg/strings/#pkg-examples)が豊富なのでそれを見ると良いです

---

# 標準パッケージ紹介

## [time](https://golang.org/pkg/time/)

* 日付・時刻のパッケージ
* [公式のExamples](https://golang.org/pkg/time/#pkg-examples)

---

# Vendoring

* go 1.5からVendoringの機能が追加され、1.6から標準になりました
* 依存しているパッケージのソースを`vendor`ディレクトリ配下に置きます
* ツールはたくさんある状態なので、いろいろと試してみると良いです
    * <https://github.com/golang/go/wiki/PackageManagementTools>
    * [tools/godep](https://github.com/tools/godep)
    * [Masterminds/glide](https://glide.sh/)
    * [FiloSottile/gvt](https://github.com/FiloSottile/gvt)
    * [kardianos/govendor](https://github.com/kardianos/govendor)
    * [constabulary/gb](https://getgb.io/)

---

# 課題

## 課題1

* チャットに発言できるクライアントを作ろう
* たぶんMattermostでやることになる
* 参考: [Mattermost APIs](http://docs.mattermost.com/developer/api.html)

---

# 課題

## 課題2

* チャットの特定のルームの発言を全てログに出力するデーモンを作ろう

---

# 課題

## 課題3

* チャットのあるルームの発言を別のルームに流すデーモンを作ろう

---

# 課題

## 課題4

**余裕のある人向け**

* コマンドで監視するルームと書き込むルームを制御できるようにしよう
* チャットからコマンドを実行できるとさらに良い
* キーワードフィルタとか好きな機能を増やして良い
* やりすぎるとチャット死ぬので気をつけてください
