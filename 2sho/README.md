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
