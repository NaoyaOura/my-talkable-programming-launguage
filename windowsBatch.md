hello world
---------------------------

```bat
echo "Hello World"
```

## コメントアウト

* 複数行にわたるコメントアウトはない

```bat
@Rem 一行コメント
:: 一行コメント
```

順次（表示・型・配列）
----------------------------------

## 標準出力

```bat
echo moji
:: ↓空行表示
echo .
```

* 変数

```bat
::定義
set str=5
::数式で定義可能
set /A i=5
::以下のような計算も同じ
set /A i=2+3
```

* 文字列操作
    * [参考：サブルーチン](http://piyopiyocs.blog115.fc2.com/blog-entry-898.html)

```bat
set str=hohoge!!
echo %str%
:: hohoge!!
echo %str:~2%
:: hoge!!
echo %str:~2,5%
:: hoge!
echo %str:~2,-2%
:: hoge!
```

* format表示（存在しない）

## 変数の扱い

* 型変換・型表示
    * 型なし

* 配列は存在しない。擬似的な配列のみ存在する

配列もどきの定義は以下

```bat
for /L %%i in (0,1,10) do set x[%%i]=%%i
echo x[0]=%x[0]%
echo x[1]=%x[1]%
echo x[2]=%x[2]%
echo x[3]=%x[3]%
```

分岐
-------------------------------

* if文

```bat
@echo off
set /A score=50
if %score% GTR 40 (
	echo ok1
	echo ok2
)
:: カッコがないときは、同行のみ実行される
if %score% GTR 60 echo ng
	:: インデントは意味をなさない
	echo ok3
:: elseはifと同じ行に書くこと
if %score% GTR 60 (echo ng) else (echo ok4)

:: コンソール
:: ok1
:: ok2
:: ok3
:: ok4
```

* 比較演算子

| 演算子  |         意味        |
|---------|---------------------|
| A EQU B | 等しい( = )         |
| A NEQ B | 等しくない( NOT = ) |
| A LSS B | ～より小さい( < )   |
| A LEQ B | ～以下( <= )        |
| A GTR B | ～より大きい( > )   |
| A GEQ B | ～以上( >= )        |


* switch文
     * なし

繰り返し
---------------------------------

* for文（一定回数の繰り返し）


```bat
for /L %%i in (0,1,4) do echo %%i
:: [コンソール]
:: 0
:: 1
:: 2
:: 3
:: 4
```


* for文（リスト繰り返し:拡張for）
    * なし（配列がそもそも存在しない）

* while文
    * なし

windowsバッチの環境変数
================================

よく利用する動的環境変数
---------------------------

|         環境変数        |                                  意味                                 |
|-------------------------|-----------------------------------------------------------------------|
| %CD%                    | 現在のディレクトリ文字列に展開します。                                |
| %DATE%                  | DATEコマンドと同じフォーマットで現在の日付に展開します。              |
| %TIME%                  | TIMEコマンドと同じフォーマットで現在の時刻に展開します。              |
| %RANDOM%                | 0 から 32767 の間の任意の 10 進数に展開します。                       |
| %ERRORLEVEL%            | 現在の ERRORLEVEL の値に展開します。                                  |

よく利用する環境変数
----------------------------

|         環境変数         |           意味           |
|--------------------------|--------------------------|
| %SystemDrive%            |                          |
| %TEMP%                   |                          |
| %TMP%                    |                          |
| %USERNAME%               |                          |
| %USERPROFILE%            |                          |
| %PROCESSOR_ARCHITECTURE% | 32,64bitを切り分けられる |


32bitか64bit判定
----------------------------

* [参考:環境変数を使ってプロセスが 64bit か 32bit か判別する](http://blog.livedoor.jp/moya_pro/archives/26944903.html)

```bat
if "%PROCESSOR_ARCHITECTURE%" == "x86" (
    if "%PROCESSOR_ARCHITEW6432%" == "AMD64" (
        echo 32bit process on 64bit OS - WOW64
    ) else (
        echo 32bit process on 32bit OS
    )
) else (
    echo 64bit process on 64bit OS
)
```

Windowsバッチでよく利用するコマンド
==================================

* 色変更（color）

```bat
:: 黒背景の緑文字にできる
color 0A
:: 赤背景に赤文字
color 4C
:: 標準の背景色
color 07
```

* 非同期実行（start）

```bat
::カレントフォルダをエクスプローラで開く
start .
::カレントフォルダでもう一つコマンドプロンプトを立ち上げる
start
::非同期でコマンドを実行(↓例では、計算機を立ち上げる)
start calc
```

* バッチファイル実行(call)

```bat
:: C:\test.batを実行する
call C:\test.bat
```

* ファイルの存在確認(if exist)

```bat
if exist "C:\Program Files" echo exist!
if exist "C:\Program File" echo not exist
```

* バッチ実行時にそのままコマンドプロンプトを開いたままにする（cmd /k）

```bat
::　バッチの最後に以下をつける
cmd /k
```

外部ファイルの読み書き
======================================

* [参考：外部ファイルの読み書き](http://capm-network.com/?tag=Windowsバッチファイル外部ファイルの読み書き)

