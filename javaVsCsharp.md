# java vs Csharp コーディング比較表


|          意味          |                java                |                                C#                                |
|------------------------|------------------------------------|------------------------------------------------------------------|
| パッケージ構成定義         | package                                | namespace ※日本語だと名前空間という                              |
| パッケージのインポート        | import                                    | using ※完全に同じではなく、pythonのusingのほうが近い(fromもある) |
| 標準出力               | System.out.println("hoge");        | Console.WriteLine("moji");                                       |
| 型判定                 | instanceof                         | is                                                               |
| 型変換                 | Integer.parseInt("5");             | int.Parse("5");                                                  |
| 配列の中身を表示         | Arrays.toString(array);              | string.Join(",", array)                                          |
| foreach                | for(String str: array){}           | foreach(String str in array){}                                   |
| Map                    | new Map<String,String>();          | new Dictionary<String,String>();※重複はエラー                    |
| クラスの継承           | extends                              | :                                                                |
| interfaceの継承          | impliments                         | :                                                                |
| javadocの記載          | /** reference */                   | /// reference                                                    |
| 親クラスの参照         | super                                | base                                                             |
| 親クラスの参照         | super                                 | base                                                             |
| final                  | final                              | readonly                                                         |
| 定数                   | public static final int CONST = 0; | public const int CONST = 0;                                      |
| static initializer     | class Class{static{ /*処理*/}}     | class Class{static Class(){ /*処理*/ }}                          |

* [Refelence-オブジェクト倶楽部 C#コーディング標準](http://so-zou.jp/software/tech/programming/tech/coding-standard/data/csharp-coding.pdf)

## javadocのタグの違い

|        |           Java          |                       C#                      |
|--------|-------------------------|-----------------------------------------------|
| 概要   | 概要                    | <summary>概要</summary>                       |
| 引数   | @param 変数名 詳細      | <param name="変数名">詳細</param>             |
| 戻り値 | @return 詳細            | <returns>詳細</returns>                       |
| 例外   | @throws 例外名 例外詳細 | <exception cref="例外名">例外詳細</exception> |
| 参照   | @see 詳細               | <see>詳細</see>                               |

* [C#-XMLDocumentの書き方](http://ufcpp.net/study/csharp/sp_xmldoc.html)
* [C#(公式)-ドキュメント コメント用の推奨タグ](https://msdn.microsoft.com/ja-jp/library/5ast78ax.aspx)

## 命名規約の違い

|                      |      Java      |      C#      |
|----------------------|----------------|--------------|
| 名前空間(パッケージ) | packagename    | NameSpace    |
| ファイル名           | ClassName.java | ClassName.cs |
| クラス名             | ClassName      | ClassName    |
| インターフェース名   | Interface      | IInterface※1 |
| プロパティ           | ---※3          | Property     |
| 定数名               | CONST          | Const※2      |
| public変数名         | valueName      | ValueName    |
| private以外の変数名   | valueName      | _valueName    |
| その他の以外の変数名   | valueName      | valueName    |
| メソッド名           | getLast        | GetLast      |

* ※1:C# では I で始まる名前
* ※2:キャメルケースで書く人と大文字スネークケースで書く人と２流派いる？
* ※3:javaでいえばaccesser(getter,setter)をもつ変数値のこと
