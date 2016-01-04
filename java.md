hello world
--------------------------


```java
public class MainClass {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

## コメントアウト

```
// 一行コメント

/*
複数行コメント
*/

```

順次（表示・型・配列）
---------------------------

## 標準出力

```java
System.out.println("moji");
```

* 変数

```java
// プリミティブ型（端的にいうと値）
// 代入時に値が参照されないという特徴をもっている
int i = 5;
float f = 5f;
boolean b = true;
// ラッパークラス
// プリミティブ型をオブジェクトにしてプリミティブ型の操作を容易にさせるもの
Integer i2 = 5;
Float f2 = 5f;
Boolean b2 = true;
// 汎用的な型
Object str1 = "hoge";
// 一般的な文字列型
String str2 = "futa";
```

* 文字列操作

```java
String str = "hohoge!!"; //文字列定義
System.out.println(str.length()); //hogege!!と表示される
System.out.println(str.substring(0, str.length())); //8と表示（文字列の長さが表示）
System.out.println(str.substring(2, 7)); //hohoge!!と表示(indexの0番目から最終行まで取得)
System.out.println(str.substring(2, str.length()-1)); //hoge!と表示
```

* format表示

```java
System.out.printf("hoge:%d%n",10);                 // hoge:10
System.out.printf("hoge:%10d%n",10);               // hoge:        10
System.out.printf("hoge:%010d%n",10);              // hoge:0000000010
System.out.printf("hoge:%f%n",10.123);             // hoge:10.123000
System.out.printf("hoge:%.2f%n",10.123);           // hoge:10.12
System.out.printf("hoge:%s%n","moji");             // hoge:moji
System.out.printf("hoge:%s, %d %n","moji",10);     // hoge:moji, 10
System.out.printf("hoge:%2$s, %1$s %n","moji",10); // hoge:10, moji 
```

## 変数の扱い

* 型変換
    * 主にラッパー(大文字の)クラスを利用して行う
    * ただの数値型などはプリミティブ型とよばれて値なので、メソッドをもたない

```java
int i = 5 + Integer.parseInt("5");
float f = 5 + Float.parseFloat("5");
String s1 = String.valueOf(5) + "5";
String s2 = 5 + "5"; // 55
```

* 型表示
     * javaはinterface定義されているため、基本的に型表示する必要性が低い

```java
// オブジェクト型であれば、表示可能
String str = "hoge";
Integer i = 5;
String[] array = {"1", "2"};
System.out.println(str.getClass()); // class java.lang.String
System.out.println(i.getClass()); // class java.lang.Integer
System.out.println(array.getClass()); // class [Ljava.lang.String;
// プリミティブ型は、型表示不可
//    int i2 = 5;
//    System.out.println(i2.getClass()); コンパイルエラー
System.out.println(str instanceof String); //true
System.out.println(str.getClass().isInstance(new String())); //true
System.out.println(array instanceof String[]); //true
System.out.println(array.getClass().isArray()); //true
```


* 配列の基本

```java
int[] array = {5, 5, 10};
System.out.println(array); // [I@2a139a55　オブジェクトの参照Codeが表示
// 配列 -> 文字列
String str = Arrays.toString(array);
System.out.println(str); //[5, 5, 10]
// javaの文字列結合はシンプルな方法が画一的に存在しないが、
// java8であれば、StringJoinerなどstreamAPIなどでの変換も可能
StringJoiner stringJoiner = new StringJoiner(",");
for(int i:array){
	stringJoiner.add(String.valueOf(i));
}
String str2 = stringJoiner.toString();
System.out.println(str2); //5,5,10
// 文字列 -> 配列
String[] array2 = str2.split(",");
System.out.println(Arrays.toString(array2)); // [5, 5, 10]
// その他の配列操作
System.out.println(array.length); // 3と表示
System.out.println(array[2]); //10
array[2] = 20;
System.out.println(Arrays.toString(array)); //[5, 5, 20]
int i = Arrays.binarySearch(array, 2); // 2が存在するかチェック
System.out.println(i); //存在しないので-1
```

* 配列の並び替え

```
int[] array = {80, 100, 30, 20};
Arrays.sort(array);
System.out.println(Arrays.toString(array)); // [20, 30, 80, 100]
```

分岐
---------------------------

* if文

```java
int score = 50;
if(score > 40){
	System.out.println("ok1");
	System.out.println("ok2");
}
// ↓【注意】javaではif・for文も中括弧無しでの記載は好ましくない
if(score > 60)
	System.out.println("ng"); // ここはif文でNGなので実行しない
	System.out.println("ok3"); //　表示される（インデントは関係ない）		

if(score > 60){
	System.out.println("ng");
}else if(score > 55){
	System.out.println("ng");
}else{
	System.out.println("else ok");
}

// and複数条件(&で書くこともできるが、意味が違うので注意※あまり使わない)
if(score > 40 && score < 60){
	System.out.println("ok4");
}

// or複数条件(|で書くこともできるが、意味が違うので注意)
if(score > 80 || score  <70){
	System.out.println("ok5");
}
// [コンソール]
// ok1
// ok2
// ok3
// else ok
// ok4
// ok5
```

* switch文

```java
String str = "hoge";
switch (str) {
case "hoge": System.out.println("hoge");
// breakをいれないと、以下がそのまま実行される
case "fuga": System.out.println("fuga");
break;
case "piyo": System.out.println("piyo");
break;
default: System.out.println("default");
}
// [コンソール表示]
// hoge
// fuga
```

繰り返し
----------------------

* for文（一定回数の繰り返し）

```java
for(int i = 0; i < 5 ; i++){
	System.out.println(i);
}
// [コンソール]
// 0
// 1
// 2
// 3
// 4

```

* for文（リスト繰り返し:拡張for）

```java
int[] array = {10, 20, 30, 40};
for(int data : array){
	if(data == 10){
		continue;// 戻る
	}
	if(data == 30){
		break; //if文から脱出
	}
	System.out.println(data);
}
// [コンソール]
// 20
```

* while文

```java
int i = 1;
while (i < 5) {
	System.out.println(i);
	i ++;
}
// [コンソール]
// 1
// 2
// 3
// 4

```

関数定義
----------------------

クラス定義
----------------------

クラスの継承
----------------------

配列以外のListオブジェクト（言語仕様）
--------------------

* List
* Queue

集合型Setオブジェクト（言語仕様）
--------------------

* Set

辞書式Mapオブジェクト（言語仕様）
----------------------------

* Map

ファイルIO
----------------------

* IOStream
* NIO2

例外処理
----------------------

### 例外処理の3分類

1. Error
    * 例外処理は任意
2. RuntimeException
    * 例外処理は任意
3. Runtime以外のException
    * 例外処理が必須


### 例外クラスの例

|        カテゴリ        |             Class名            |                          発生パターン                          |
|------------------------|--------------------------------|----------------------------------------------------------------|
| Error                  | AssertError                    | assert文を使用しているときに、falseが返ったとき                |
|                        | ExceptionInInitializer         | staticイニシャライザで予想外の処理が行われたとき               |
|                        | StackOverflowError             | アプリケーションでの再起の回数が多すぎるとき                   |
|                        | NoClassDefFoundError           | 読み込もうとしたクラスファイルが見つからないとき               |
| RuntimeException       | ArrayIndexOutOfBoundsException | 不正なインデックスで要素にアクセスしたとき                     |
|                        | ClassCastException             | 参照変数において誤ったキャストを行ったとき                     |
|                        | IllegalArgumentException       | メソッドの引数に不正なものを利用したとき                       |
|                        | IleegalStateException          | メソッド呼び出しが正しくない状態で行われたとき                 |
|                        | NullPointerException           | nullが代入されている参照変数に対して、呼び出しをおこなったとき |
|                        | NumberFormatException          | 整数でない文字列に整数変換を行ったとき                         |
| Runtime以外のException | IOException                    | 入出力を行うとき                                               |
|                        | FileNoFoundException           | inputファイルが存在しないとき                                  |
|                        | ClassNotFoundException         | クラス名を表す文字列を引数にしたが、見つからなかったとき       |


* throwsキーワードをもつメソッドのoverride
    * サブクラスのメソッドがスローする例外は、スーパークラスのメソッドがスルーする例外クラスと同じか、その例外クラスのサブクラスとする
    * サブクラスのメソッドがスルーする例外は、RuntimeExceptionおよびRuntimeExceptionのサブクラスの例外はスーパークラスのメソッドに関係なくスローできる
    * スーパークラスのメソッドにthrowsがあっても、サブクラス側でthrowsを記述しないことは可能

interface
----------------------

* interface
    * 変数はpublic static finalが暗黙的に追加
    * メソッドはpublic abstractが暗黙的に追加

Thread処理
----------------------



特性的に備わった機能
========================

Stream(java8から実装)
----------------------

