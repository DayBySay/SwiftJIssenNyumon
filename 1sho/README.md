# Swiftの特徴
## 静的型月言語であること
* コンパイル時に方の情報を決定する
* ランタイムエラーではなくコンパイル時に検知できるエラーが動的型付けに比べて増える為、安全性を高めたい大規模開発に向いている
## nil許容性のコントロールができる
* nilとして扱っている変数へのアクセス箇所などがバグりやすい
* 基本的にnilを代入することは出来ないようになっている
* nilを扱う場合はOptional型を利用する
* 値の有無がコンパイル時に決まるのでより安全になる
## 型推論
* 実装上型を明示しなくても良いので簡潔に書ける
## ジェネリクス
* 型に制約されない柔軟なプログラムを書く方法
* プロトコルを利用し、型の安全性を担保している
* 引数に型を明示しないので、型ごとに関数を定義する必要がなくなる
## ObjCとの連携
* CocoaはObjCで書かれている
* SwiftはObjCと連携可能なので、Cocoaの資産が使える

# cli
## REPL
```
➜  1sho git:(1sho) swift
Welcome to Apple Swift version 4.1 (swiftlang-902.0.48 clang-902.0.39.1). Type :help for assistance.
  1> var a = 123
a: Int = 123
  2> a = "abc"
error: repl.swift:2:5: error: cannot assign value of type 'String' to type 'Int'
a = "abc"
    ^~~~~


  2> :exit
```

## swift command
* swiftcで複数ファイルから1プログラムをコンパイルする場合、`main.swift`というファイル名をエントリポイントにする
* `main.swift`以外のファイルのトップレベルには定義しか書けない

# Swift OSS
* SwiftはOSSで開発されている
* コンパイラやライブラリ群も
* XcodeやCocoaは非OSS

## ライブラリ
* 標準ライブラリ
    * 数値や文字列など、import不要なもの
* コアライブラリ
    * Foundation
    * libdispatch
    * XCTest

## 開発ツール
* Swift Package Manager
    * Package Management System
* LLDB
    * デバッガ
    * プログラムの対話的実行や変数、コールスタックのダンプ等が出来る

# 命名規則
* 単語の区切り
    * UpperCamel
* 単語の選び方
    * 曖昧さを避ける
        * `findUser(_:)` -> `findUser(byID:)`
        * 何を使って検索するかが曖昧なので明示する
    * 一般的な単語を使う
        * `epidermis` -> `skin`
        * 同じ意味の単語があればわかりやすいほうを使う
    * 略語を避ける
        * `stmt` -> `statement`
        * `stmt`じゃわからん
    * 詳しくは[API Design Guideline](https://swift.org/documentation/api-design-guidelines/)を参照

# まとめ
* Swiftは簡潔な文法 + 型の安全性を持った言語
* 型安全の特徴を活かすためには仕様を理解しよう
