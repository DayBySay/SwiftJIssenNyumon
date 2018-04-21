# 変数と定数
* 再代入可能かどうかの違い
* 定数を使うと意図しない値の更新を防げる

## 宣言
```swift
var a: Int = 123 // 変数
let b: Int = 123 // 定数
     // ↑ 型アノテーション

a = 456 // ok
b = 456 // ng
```

* 型アノテーションは、基本的には推論に任せると良い

### 型の確認
* `type(of: )` を使う

```shell
➜  2sho git:(2sho) ✗ swift
Welcome to Apple Swift version 4.1 (swiftlang-902.0.48 clang-902.0.39.1). Type :help for assistance.
  1> let a = 123
a: Int = 123
  2> type(of: a)
$R0: Int.Type = Int
```

### 宣言時に型を定義
* 型アノテーションも代入もないと型が決められないのでエラー

```swift
let a // ng
```

#＃ 代入
* 一致した型の値のみ代入可能
* 変数定数が使用されるまでに値を代入しないといけない
* 定数には再代入できない

## スコープ
* 定義した変数などの有効範囲
* グローバルとローカルのどちらかに所属

### ローカルスコープ
* 局所的
* 意図しない変更が起こりづらい

### グローバルスコープ
* プログラム全体からアクセス可能
* 意図しない変更を起こしやすい

## 基本的な方
### 浮動小数点型
* floatとdoubleで精度が違うので注意
* 画面のサイズとかはfloatだけど座標を扱う場合はdoubleなど使い分けられている
* infinityやNaN(Not a Number)など特殊はプロパティを持っている
* 同じ整数でも型が違えば代入できない、それをする場合はイニシャライザを用いたキャストを行う

## 操作
* 比較演算子、算術演算子がいろいろある。細かいことは割愛

## 文字列リテラル
### 特殊文字

```swift
let lf = "\n"
let cr = "\r"
let null = "\0"
```

など

### 文字列リテラル内の値の展開

 ```swift
 let a = 111
 let out = "\(a)" // 111
```

### 複数行

```swift
let a = """
aaaa
  aaaaa
aaaa
"""
```

### Stringの個々の文字について
* Character型で表される

```swift
let string = "a"
let character: Character = "a"

type(of: string)
type(of: character)
```

* 文字列内の個々のCharacterの一はString.Indexで表される

```swift
let a = "12345"
print(a.startIndex) // 0
print(a.endIndex) // 20
```

* Indexを使ってアクセスできる
* endIndexは最後の次の要素を指してしまうので注意
* 途中の値を取るにはoffsetby

```swift
let a = "12345"
print(a[a.startIndex]) // 1
print(a[a.endIndex]) // Fatal error: Can't form a Character from an empty String
print(a[a.index(a.startIndex, offsetBy: 2)]) // 3
print(a[a.index(a.endIndex, offsetBy: -2)]) // 4
```

### 文字列の比較
* `==`でOK
* 型違いは比較できない, String, Character同士など

### 結合
* `+`
* `append`を使うとString + Characterがいける

### 高度な操作
* 文字列の順番を比較する関数とかがFoundationにある


## Array
* シンタックスシュガーあり`Array<Int>`->`[Int]`
* 複数の要素を含む場合は`Any`を明示
* 基本は型推論が効く
* `let a = [[1,2,3], [1,2,3]]` -> `[[Int]]`

## Dictionary
* シンタックスシュガー `Dictionary<String, Int>` -> `[String: Int]`
* からの辞書 `[:]`
* Keyに入れる型は`Hashable`に準拠している必要あり
* Valueはなんでもおｋ

## 範囲型
* `Range<Bound>`など
* 終了を含んだり含まなかったりするタイプがある

```swift
let range1 = 1..<10
for i in range1 {
    print(i) // 1...9まで出力
}
type(of: range1) // CountableRange<Int>.Type

let range2 = 1...10
for i in range2 {
    print(i) // 1...10まで出力
}
type(of: range2) // CountableClosedRange<Int>.Type
```

## Optional
