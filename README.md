
# my-talkable-programming-launguage

せっかく習得した言語も利用しないと、他の言語と混ざって忘れてしまうので、  
自分のために、それぞれの言語を横並びに相違点などをまとめていく

--------------------------------------------------------------------------------------

## Python

### 特徴

------------

* スクリプト言語
* 世界的に一般的なスクリプト言語
* ifやfor、関数やクラス定義もインデントを使ったブロックの表現で制御。
* PerlやRubyが様々な方法で実装できるのに対して、Pythonはやり方を1つだけ用意するようにしている
* 簡潔で見やすいコードを書きやすい。
* 2系と3系のバージョン違いに、しばしば混乱する（2系と3系で標準出力の方法が違ったりライブラリが使えなかったりと混乱する）

### 目的別利用パターン

----------------

* ライブラリも充実していて、スクリプト言語として簡単なプログラムも書きやすい
* 幾何学的な解析に強い(pandasやR関連のライブラリも充実している)

### コーディング規約

----------------

* [Google Python スタイルガイド](http://works.surgo.jp/translation/pyguide.html)
* [PEP8 日本語訳](http://pep8-ja.readthedocs.org/ja/latest/)

### 基本的な文法

----------------

* [python3系](python.md)
     * まとめ中

--------------------------------------------------------------------------------------

## Java

### 特徴

------------

* インタプリタ言語で、実行にはVMを立ち上げる時間がかかるが、実行速度は早い
* 実行速度はCには及ばないものの、GC（ガベージコレクション）付きかつカーソルなどの考慮もいらない言語として非常に早い
* 型宣言がとても手堅く、バグが起こりづらいソースコードになりやすいが、コード量が多い
     * 慣れるまでには、ソースコードを書くことに時間がかかるデメリットにもなるが、慣れれば反対に型がゆるいプログラミング言語が嫌にもなる
* WindowsだろうがLinaxだろうがJVM上で動くので実行環境に依存しない


### 目的別利用パターン

----------------

* 手堅く常時動くようなシステム（基幹系システムなど）に向く
* ライブラリやFWも充実しているため、大体の目的はjavaで達成できるため、プログラミング初学者にもおすすめ

### コーディング規約

------------

* [Java コーディング標準 - オブジェクト倶楽部](http://objectclub.jp/community/codingstandard/CodingStd.pdf)
* [Google Java Style](http://google-styleguide.googlecode.com/svn/trunk/javaguide.html)
* [Java セキュアコーディングスタンダード](https://www.jpcert.or.jp/java-rules/)

### 基本的な文法

------------

* [java](java.md)
     * まとめ中

--------------------------------------------------------------------------------------


## Scala

### 特徴

* Java並の手堅い言語仕様とRuby並の書きやすさが両立したような言語仕様
    * ただし、両方の特徴をもつためjavaやRubyと比較するととてもむずかしい（習得に非常に時間がかかるため、大規模開発には向かない）
* JVM上で動くため以下の特徴もある（コンパイルするとclassファイルが作成される）
	* インタプリタ言語で、実行にはVMを立ち上げる時間がかかるが、実行速度は早い
	* 実行速度はCには及ばないものの、GC（ガベージコレクション）付きかつカーソルなどの考慮もいらない言語として非常に早い
	* WindowsだろうがLinaxだろうがJVM上で動くので実行環境に依存しない

------------

### コーディング規約

------------

* [Scalaスタイルガイド](http://yanana.github.io/scala-style/)
* [Effective Scala](http://twitter.github.io/effectivescala/index-ja.html)

### 基本的な文法

------------

* [scala](scala.md)
     * まとめ中

--------------------------------------------------------------------------------------


## CSharp（C#）

### 特徴

* 別名C++++や++C++。実際のところ文法もjavaそっくり（※中間コードに翻訳してJVM上で動作する）
	* javaプログラマーにはとっつきやすいが、インデクサやデリゲート、LinQ、ライブラリ管理などはjavaと異なる点も多々ある
* windowsで動くアプリケーション向き（Linax動作などは不向き）で、GUI（通称Formアプリケーション）のあるアプリケーションが非常に簡単につくれる
* Windows関連のアプリケーション操作（Excelなど）も強く書きやすい。ExcelVBAをjavaのようなオペレーションで書くこともできるし、VBAそのもののように操作することもできる
    * POIでは対応しきれないところも、C#であれば簡単に対応できることが多い
* windows上であれば、実行環境の用意が基本的にいらない（※開発環境は別）

------------

### コーディング規約

------------


* [C# のコーディング規則 (C# プログラミング ガイド) | Microsoft](https://msdn.microsoft.com/ja-jp/library/ff926074.aspx)

### 基本的な文法

------------



* [C#](csharp.md)
     * まとめ中

--------------------------------------------------------------------------------------

## php

## ruby

## ExcelVBA

## VBScript

## windowsBat

## shell

## oracleSQL

### 特徴

* SQLなので、手続き型言語ではない
* 非常に高速かつ高価なRDBとして利用されるOracleDBにたいするSQL
* 11g(byte)までであれば、無料での利用が可能

### 基本的な文法

------------

* [oracleSQL](oracleSQL.md)
     * まとめ中