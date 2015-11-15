hello world
--------------------------

```scala
object test {
  def main(args: Array[String]): Unit = {
    println("Hollo World")
  }
}
```

## コメントアウト

```scala
// 一行コメント

/*
複数行コメント
*/
```

順次（表示・型・配列）
---------------------------

## 標準出力

```scala
println("moji")
```

* 変数

```scala
// 型推論（型を明示しない）
var str1 = "hoge"
// 再代入不可となる型
val str2 = "fuga"
// 型宣言をする方法
var str3 : String = "piyo"
```

* 文字列操作

```scala
// var str = "hohoge!!"でもOK
var str : String= "hohoge!!"
println($str)
println(str.length());  //8と表示される
println(str.substring(0)) //hohoge!!と表示(indexの0番目から最終行まで取得)
println(str.substring(2, 7)) //hoge!と表示
println(str.substring(2, str.length()-1)) //hoge!と表示
```

* format表示

```scala
var no :Int = 10
var foo :Float = 10.123f
var str :String = "moji"
println(f"hoge:$no")       // hoge:10
println(f"hoge:$no%10d")   // hoge:        10
println(f"hoge:$no%010d")  // hoge:0000000010
println(f"hoge:$foo")      // hoge:10.123
println(f"hoge:$foo%.2f")  // hoge:10.12
println(f"hoge:$str")      // hoge:moji
println(f"hoge:$str ,$no") // hoge:moji ,10
println(f"hoge:$no ,$str") // hoge:10 ,moji
```

## 変数の扱い

* 型変換

```scala
var i : Int = 5 + "5".toInt
var f : Float = 5 + "5".toFloat
var s : String = 5.toString() + "5"
//var s : String = 5 + "5" error
```

* 型表示

```scala
var str = "5"
var str2 :String = "5" // 型定義はダブルコロン
println(1.getClass()) // int
println(str.getClass()) // class java.lang.String
println(str2.getClass()) // class java.lang.String
println(str.isInstanceOf[String]); //true
```

* 配列の基本

```scala
var array = Array(5, 5, 10)
println(array) // [I@4aa298b7 オブジェクトの参照Codeが表示
// 配列 -> 文字列
var str = array.mkString(",")
println(str) // 5,5,10 :","はデリミタとしての役割
var str2 = array.deep.toString();
println(str2) // Array(5, 5, 10)
// 文字列 -> 配列
var array2 = str.split(",")
println(array2.mkString(","))
// その他の配列操作
println(array.length) //3と表示
println(array.size) //3と表示
println(array(2)) // 10 と表示
array(2) = 20
println(array.mkString(",")) // 5,5,20
var b = array.contains(2) // 2が存在するかチェック
println(b) // falseと表示
```

* 配列の並び替え

```scala
var array = Array(80, 100, 30, 20)
Sorting.stableSort(array)
println(array.mkString(",")) // 20,30,80,100
```

分岐
---------------------------

* if文

```scala
val score = 50;
if (score > 40) {
  System.out.println("ok1");
  System.out.println("ok2");
}
// ↓【注意】javaではif・for文も中括弧無しでの記載は好ましくない
if (score > 60)
  System.out.println("ng"); // ここはif文でNGなので実行しない
System.out.println("ok3"); //　表示される（インデントは関係ない）		

if (score > 60) {
  System.out.println("ng");
} else if (score > 55) {
  System.out.println("ng");
} else {
  System.out.println("else ok");
}

// and複数条件(&で書くこともできるが、意味が違うので注意※あまり使わない)
if (score > 40 && score < 60) {
  System.out.println("ok4");
}

// or複数条件(|で書くこともできるが、意味が違うので注意)
if (score > 80 || score < 70) {
  System.out.println("ok5");
}
```

* match文（switch文以上の役割ももつ）

```scala
val x:Any = 5;
x match{
  // javaでいうbreakの記載は不要
  case 0 => println("x = 0")
  case 5 => println("x = 5")
  // 型による分岐も可能
  case s:String => println("x:String")
  // 追加でif文も追加可能
  case i:Int if i > 100 => println("x over 100")
  // javaのswitch文でいうdefault
  case _ => println("no match")
}
```

繰り返し
------------------------

* for文（一定回数の繰り返し）

```scala
for (i <- 0 to 4) {    
  println(i)
}
// [コンソール]
// 0
// 1
// 2
// 3
// 4
```

* for文（リスト繰り返し:拡張for）

```scala
var array = Array(10, 20, 30, 40)
for (data <- array) {
  println(data)
}
// [コンソール]
// 10
// 20
// 30
// 40

//continueは存在しない
for (data <- array if data != 10){
  println(data)
}
// [コンソール]
// 20
// 30
// 40

// breakを利用するとき
// import scala.util.control.Breaks
var b = new Breaks
b.breakable{
  for(data <- array if data != 10){
    println(data)
    if(data == 30){
      b.break
    }
  }
}
// [コンソール]
// 20
```


* while文

```scala
var i = 1
while(i < 5){
	println(i)
	// scalaはインクリメント不可
	i += 1
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

集合型Setオブジェクト（言語仕様）
--------------------

辞書式Mapオブジェクト（言語仕様）
----------------------------

ファイルIO
----------------------

例外処理
----------------------

interface
----------------------

Thread処理
----------------------


