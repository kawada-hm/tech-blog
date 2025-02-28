---
layout: post
title: "JavaScript基礎：変数とデータ型"
date: 2025-02-25 09:00:00 +0900
categories: programming
---

## JavaScriptの変数宣言

JavaScriptでは、変数を宣言するための3つのキーワードがあります：`var`、`let`、`const`です。

### var

```javascript
var name = "John";
```

`var`は関数スコープを持ち、再宣言と再代入が可能です。しかし、現代のJavaScriptでは`let`と`const`の使用が推奨されています。

### let

```javascript
let age = 25;
age = 26; // 再代入可能
```

`let`はブロックスコープを持ち、再宣言はできませんが再代入は可能です。

### const

```javascript
const PI = 3.14159;
// PI = 3.14; // エラー：constは再代入不可
```

`const`もブロックスコープを持ち、再宣言も再代入もできません。ただし、オブジェクトや配列の内容は変更可能です。

## JavaScriptのデータ型

JavaScriptには以下の基本データ型があります：

1. **プリミティブ型**
   - 文字列（String）
   - 数値（Number）
   - 真偽値（Boolean）
   - undefined
   - null
   - シンボル（Symbol）
   - BigInt

2. **参照型**
   - オブジェクト（Object）
   - 配列（Array）
   - 関数（Function）
   - 日付（Date）
   - 正規表現（RegExp）

### 例：データ型の確認

```javascript
typeof "Hello"; // "string"
typeof 42; // "number"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof null; // "object" (JavaScriptの有名なバグ)
typeof Symbol(); // "symbol"
typeof {}; // "object"
typeof []; // "object" (配列もオブジェクトの一種)
typeof function(){}; // "function"
```

## まとめ

JavaScriptの変数宣言とデータ型の基本を理解することは、効果的なJavaScriptプログラミングの第一歩です。現代のJavaScriptでは、`var`よりも`let`と`const`を使用することが推奨されています。
