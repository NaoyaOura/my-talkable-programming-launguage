hello world
--------------------------

```cs
namespace ConsoleApplicationTest
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World");
            Console.ReadKey();
        }
    }
}
```

## コメントアウト

```cs
// 一行コメント

/*
複数行コメント
*/

```

順次（表示・型・配列）
---------------------------

## 標準出力

```cs
Console.WriteLine("moji");
```

* 変数

```cs
// リテラルはすべて小文字
bool b = true;    // 論理値リテラル
int n = 26983;   // 整数リテラル
double x = 10.362;  // 実数リテラル
char c = 'a';     // 文字リテラル
string s = "文字列"; // 文字列リテラル

// 型推論(型を明示しない)
var x = 10;
// ただし右辺がないときは利用不可
var y;
//y = 10; コンパイルエラー
```

* 文字列操作

```cs
string str = "hohoge!!";
Console.WriteLine(str.Length);
Console.WriteLine(str.Substring(0));
Console.WriteLine(str.Substring(2, 5));
Console.WriteLine(str.Substring(2, str.Length - 3));
```

* format表示
    * [chartSheet](http://www.dylanbeattie.net/cheatsheets/dot_net_string_format_cheat_sheet.pdf)


```cs
Console.WriteLine("hoge:{0:D}", 10);            // hoge:10
Console.WriteLine("hoge:{0,10}", 10);           // hoge:        10
Console.WriteLine("hoge:{0:D10}", 10);          // hoge:0000000010
Console.WriteLine("hoge:{0:0000000000}", 10);   // hoge:0000000010
Console.WriteLine("hoge:{0:f}", 10.123);        // hoge:10.12
Console.WriteLine("hoge:{0:0.0000}", 10.123);   // hoge:10.1230
Console.WriteLine("hoge:{0:0.####}", 10.123);   // hoge:10.123
Console.WriteLine("hoge:{0}", "moji");          // hoge:moji
Console.WriteLine("hoge:{0} ,{1}", "moji", 10); // hoge:moji ,10
Console.WriteLine("hoge:{1} ,{0}", "moji", 10); // hoge:10 ,moji
```

## 変数の扱い

* 型変換
    * それぞれの型に定義された

```cs
int i = 5 + int.Parse("5");
float f = 5 + float.Parse("5");
string s1 = 5.ToString() + "5";
string s2 = 5 + "5";
```

* 型表示

```cs
Console.WriteLine(1.GetType()); //System.Int32
Console.WriteLine("h".GetType()); //System.String
Object[] array = {1, 2};
Console.WriteLine(array.GetType()); //System.Object[]
Console.WriteLine("h".GetType() == typeof(String)); //True
```

* 配列の基本

```cs
int[] array = { 5, 5, 10 };
Console.WriteLine(array); //System.Int32[] と型の名前が表示
// 配列 -> 文字列
// 暗黙的型変換を含んでいるので、本当は、以下でarrayをstring配列に変える
// string[] arrayStr = Array.ConvertAll(array,element => element.ToString());
string str = string.Join(",", array);
Console.WriteLine(str); // 5, 5, 10
// 文字列 -> 配列
string[] array2 = str.Split(',');
Console.WriteLine(string.Join(",", array2)); // 5, 5, 10
// その他の配列操作
Console.WriteLine(array.Length); //3
array[2] = 20;
Console.WriteLine(string.Join(",", array));
int i = Array.IndexOf(array, 2);
Console.WriteLine(i); // 存在しないので-1
```

* 配列の並び替え

```
int[] array = { 80, 100, 30, 20 };
Array.Sort(array);
Console.WriteLine(string.Join(",", array)); // 20,30,80,100
```

分岐
-------------------------

* if文

```cs
int score = 50;
if(score > 40){
    Console.WriteLine("ok1");
    Console.WriteLine("ok2");
}
// ↓【注意】javaではif・for文も中括弧無しでの記載は好ましくない
if(score > 60)
    Console.WriteLine("ng"); // ここはif文でNGなので実行しない
    Console.WriteLine("ok3"); //　表示される（インデントは関係ない）     

if(score > 60){
    Console.WriteLine("ng");
}else if(score > 55){
    Console.WriteLine("ng");
}else{
    Console.WriteLine("else ok");
}

// and複数条件(&で書くこともできるが、意味が違うので注意※あまり使わない)
if(score > 40 && score < 60){
    Console.WriteLine("ok4");
}

// or複数条件(|で書くこともできるが、意味が違うので注意)
if(score > 80 || score  <70){
    Console.WriteLine("ok5");
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

```cs
String str = "hoge";
switch (str) {
case "hoge":
    Console.WriteLine("hoge");
    break;// breakをいれないとビルドエラー
case "fuga":
    Console.WriteLine("fuga");
    break;
case "piyo":
    Console.WriteLine("piyo");
    break;
default:
    Console.WriteLine("default");
    break;// breakをいれないとビルドエラー
}
// [コンソール]
// hoge

```

繰り返し
-------------------------

* for文（一定回数の繰り返し）

```cs
for(int i = 0; i < 5 ; i++){
    Console.WriteLine(i);
}
// [コンソール]
// 0
// 1
// 2
// 3
// 4

```

* for文（リスト繰り返し:拡張for）

```cs
int[] array = {10, 20, 30, 40};
foreach(int data in array){
    if(data == 10){
        continue;// 戻る
    }
    if(data == 30){
        break; //if文から脱出
    }
    Console.WriteLine(data);
}
// [コンソール]
// 20

```

* while文

```cs
int i = 1;
while (i < 5) {
    Console.WriteLine(i);
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

集合型Setオブジェクト（言語仕様）
--------------------

辞書式Mapオブジェクト（言語仕様）
----------------------------

ファイルIO
----------------------

例外処理
----------------------

Thread処理
----------------------

特性的に備わった機能
======================

インデクサ
----------------------

ファイル分割（partial）
----------------------

デリゲート
----------------------

LinQ（リンク）
----------------------

