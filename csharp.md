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

### ディレクトリ操作

* 現在のディレクトリ参照

```cs
//using System.IO;
Directory.GetCurrentDirectory();
```

* ディレクトリ作成

```cs
//using System.IO;
Directory.CreateDirectory(string path);
```

### ファイル名操作

* ファイル名を取得する
```cs
//using System.IO;
string path = @"C:\tmp\hoge.txt";
string fileNm = Path.GetFileName(path); // hoge.txt
```

例外処理
----------------------

* [Reference-例外と例外処理](https://msdn.microsoft.com/ja-jp/library/ms173160.aspx)
* [Reference-javaとの例外処理の違い](http://blogs.msdn.com/b/nakama/archive/2009/01/09/net-java.aspx)
    * C#における例外は、最終的にはすべて System.Exception から派生する型です。

|           名前空間          |           クラス名          |                                        発生パターン                                        |
| --------------------------- | --------------------------- | ------------------------------------------------------------------------------------------ |
| System                      | ArgumentNullException       | 引数がnullの場合                                                                           |
| System                      | ArgumentOutOfRangeException | メソッドの許容範囲外の値が引数として渡された場合                                           |
| System                      | ArgumentException           | メソッドの引数が変な場合(上記２つ以外の場合で変な時に使う)                                 |
| System                      | OverflowException           | 算術演算やキャストでオーバーフローが起きた場合                                             |
| System                      | DivideByZeroException       | 0で割ったときのエラー                                                                      |
| System                      | NotFiniteNumberException    | 浮動小数点値が無限大の場合                                                                 |
| System                      | ArithmeticException         | 算術演算によるエラーの基本クラス(上記３つ以外の算術エラー)                                 |
| System                      | FormatException             | 引数の書式が仕様に一致していない場合                                                       |
| System                      | IndexOutOfRangeException    | 配列のインデックスが変な場合                                                               |
| System                      | InvalidCastException        | 無効なキャストの場合                                                                       |
| System                      | InvalidOperationException   | 引数以外の原因でエラーが起きた場合                                                         |
| System                      | ObjectDisposedException     | Dispose済みのオブジェクトで操作が実行される場合                                            |
| System                      | NotImplementedException     | メソッドが未実装の場合                                                                     |
| System                      | NotSupportedException       | 呼び出された機能を備えていないストリームに対して読み取り、シーク、書き込みが試行された場合 |
| System                      | NullReferenceException      | nullオブジェクト参照を逆参照しようとした場合                                               |
| System                      | PlatformNotSupportException | 特定のプラットフォームで機能が実行されない場合                                             |
| System                      | TimeoutException            | 指定したタイムアウト時間が経過した場合                                                     |
| System.Collections.Generics | KeyNotFoundException        | コレクションに該当するキーが無い場合                                                       |
| System.IO                   | DirectoryNotFoundException  | ディレクトリが無い場合                                                                     |
| System.IO                   | FileNotFoundException       | ファイルが無い場合                                                                         |
| System.IO                   | EndOfStreamException        | ストリームの末尾を超えて読み込もうとしている場合                                           |


Thread処理
----------------------

Serialize
----------------------

SerializeはC#では、大きく
0. 古典的なiniファイル形式
0. xml形式のファイル

の二つが一般的である。

# xml形式のSerialize.IOの実装例

* オブジェクトの保存

```cs
// using System.Xml.Serialization;
public static void Save<T>(T t, string path)
{
    XmlSerializer xmlSerializer = new XmlSerializer(t.GetType());
    using (FileStream fs = File.Create(path))
    {
        xmlSerializer.Serialize(fs, t);
    }
}
```

* オブジェクトのロード

```cs
// using System.Xml.Serialization;
public static T Load<T>(string path)
{
    XmlSerializer xmlSerializer = new XmlSerializer(typeof(T));
    using (FileStream fs = File.OpenRead(path))
    {
        return (T)xmlSerializer.Deserialize(fs);
    }
}
```

特性的に備わった機能
======================

メソッド引数の参照・値渡し（refとout）※VBAでいうByRefとByVAL
------------------------------------------------------

* javaでいう、プリミティブ型をメソッド引数渡ししたときには、必ず値渡しとなり、引数にうけとった値をメソッド内部で書き換えても呼び出し元の変数値に影響を与えない。  
C#では、ExcelVBA(のFunction)などと同様にメソッド引数をメソッド内部で値を変更させ、それを引数元の変数にまで影響を与えることができる。

```cs
public class Foo{
    public void exchange(int a,int b){
        int temp;
        temp = a;
        a = b;
        b = temp;
    }
    public void Foo(){
        int x = 10;
        int y = 20;
        exchange(x,y); // 値渡し
        exchange(out x,out y);  // 参照渡し
        exchange(ref x,ref y);
    }
}
```


インデクサ
----------------------

クラスインスタンスを配列のプロパティ値のように利用することができるC#独特な言語仕様。  
C#に用意されているdictionary（※javaだとMap）がこの記法にあたるためjavaプログラマーも特性を覚えることが必須。

```cs
using System;
class Boo{
    string[] strs = new string[5];
    //インデクサ -> this[indexの型　index]
    public string this[int i]                   
    {
        get{
            return strs[i];
        }
        set{
            strs[i] = value;
        }
    }
}
class Foo{
    public static void Main()
    {
        Boo boo = new Boo();
        // ↓自動的にsetterが呼ばれる
        boo[0] = "hoge";
        // ↓自動的にgetterが呼ばれる
        Console.WriteLine(boo[0]);
    }
}
```

ファイル分割（partial）
----------------------

* クラス定義の前にpartialとすることで、ファイルを分割することができる

```cs
public partial class Form1{}
```

デリゲート
----------------------

CやC++でいう関数へのポインタ。
メソッドへの参照を保存して、その参照をメソッドとして呼び出すことが可能
(シグネチャは一致している必要がある)複数定義も可能（※マルチキャストデリゲーション）
デリゲートは以下のようにメソッドの前にdelegate とつけることで定義完了

```cs
    delegate public Object MethodName(Object objectName);
```

LinQ（リンク）
----------------------

Excel IO
======================

* [Reference](http://qiita.com/kyama0922/items/f0c6449d8734889d1e83)

* 参照設定
    * Solution Explorer > Reference 右クリック> Add Reference 
        * COM > Type Library > Microsoft Excel xx.x Object Library　を選択

* Sample

```cs
// using Excel = Microsoft.Office.Interop.Excel;
string path = null;
try
{
    Excel.Application ExcelApp = new Excel.Application();
    //エクセルを非表示
    ExcelApp.Visible = false;

    //エクセルファイルのオープンとワークブック作成
    Excel.Workbook WorkBook = ExcelApp.Workbooks.Open(@"FilePath");
    path = WorkBook.Path;
    Excel.Worksheet sheet = WorkBook.Worksheets.Add();
    sheet.Name = "シート名";
    //1シート目の選択
    Excel.Worksheet sheet1 = WorkBook.Sheets[1];
    sheet1.get_Range("A1").Value = "hoge";
    // シート名指定で取得
    Excel.Worksheet sheet2 = WorkBook.Sheets["シート名"];
    sheet2.get_Range("A1").Value = "fuga";
    // Excelを保存
    WorkBook.Save();
    //ワークブックを閉じる
    WorkBook.Close();
    //エクセルを閉じる
    ExcelApp.Quit();
}
finally
{
    // 注意：＜これは最も簡便的な方法＞Excelのオブジェクトを開放し忘れているとプロセスが落ちないため注意
    GC.Collect();
}
MessageBox.Show(path);
```

開発ツール
======================

単体テストツール
----------------------

ビルドツール
----------------------

* [msbuild](https://ja.wikipedia.org/wiki/MSBuild)
    * msbuild は Microsoft 製のビルドツールです。 多くの場合は Visual Studio が生成した .csproj ファイルや .sln ファイルを直接 msbuild の対象として使う
    * Visual Studio 上で参照を追加してあれば、 これといってコマンド上で何か特別に操作する必要はない
    * msbuild 用に .csproj ファイルなどを直接編集する場合は Project の子要素 ItemGroup に Reference 要素を追加して Sample.dll を参照に加えます。

```cs
<Project ...>
    ...
    <ItemGroup>
        <Reference Include="Sample.dll" />
        ...
    </ItemGroup>
    ...
</Project>
```

* [NAnt](http://nant.sourceforge.net/)
    * `NAnt`はオープンソースの .NET 環境用ビルドツール
    * `NAnt`の場合は`csc`タスクや`vbc`タスクの子要素として references 要素を定義し、 そこで 対象のDLLを指定すれば参照に加えることができます

```
<csc ...>
    <references>
        <lib>
            <include name="..\package"/>
        </lib>
        <include name="Sample.dll"/>
    </references>
</csc>
```

テキストエディタエンジン
-----------------------

* [Azuki](http://sgry.b.osdn.me/)
    * .NET Compact Framework を含めた .NET 環境用の、 C# で作られているテキストエディタの「エンジン」です。 Visual Studio を使っていればドラッグ＆ドロップで配置できる GUI コンポーネント、ドキュメント、ビュー、シンタックスハイライターなどを提供します

<http://srad.jp/story/09/01/27/0547207/>