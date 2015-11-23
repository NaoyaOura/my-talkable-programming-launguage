hello world
--------------------------

```php
<!DOCTYPE html>
<html lang="ja">
<body>
	<p><?php echo "Hello World";?></p>
</body>
</html>
```

## ビルトインサーバーのたてかた（簡易）

0. ローカルPCのIPアドレスを取得
	* windowsであれば、 ```ipconfig /all``` で取得可能
0. 実行するディレクトリで、

```php
// 0.0.0.0のところは、自身のIPアドレスを記載
// 8000のところは、ポート番号を指定
php -S 0.0.0.0:8000
```

実行すると、Listening on のあとにビルトインされたアドレスが出力される

## コメントアウト

```php
// 単一コメント
# 単一コメント
/*
	複数行コメントアウト
*/
```

順次（表示・型・配列）
---------------------------

## 標準出力

```php
<?php
echo "moji"
```

* 変数

```php
<?php
$message = "moji"
echo $message


// 定数を宣言したいときは、
define("CONST_MESSAGE", "build CONST!");
echo CONST_MESSAGE;

// 環境情報の表示
var_dump(__LINE__);// 行数表示の方法
var_dump(__FILE__); // file名の表示
var_dump(__DIR__); //ディレクトリ名の表示
```

* 文字列操作

```php
$word = "World";

// scalaのような標準出力が可能
echo "hello $word!"; // hello World!
echo "hello ${word}!";// hello World!
echo "hello {$word}!";// hello World!

// シングルクォートは、特殊文字を認識しない
// "" ダブルクォート：特殊文字（\m \t）などの変数も利用できる
// '' シングルクォート：特殊文字が使えない
echo 'hello $word!';// hello $word!

$word2 = "Wo" . "rld!"; //文字列連結はドット表示
echo "hello $word2"; // hello World!

$str = "hohoge!!";
echo strlen($str);

```

* format表示

```php
printf("hoge: %d"    , 10);     # hoge: 10
printf("hoge: %10d"  , 10);     # hoge:         10
printf("hoge: %010d" , 10);     # hoge: 0000000010
printf("hoge: %f"    , 10.123); # hoge: 10.123000
printf("hoge: %.2f"  , 10.123); # hoge: 10.12
printf("hoge: %s"    , "moji"); # hoge: moji
printf("hoge: %s %d" , "moji", 10); # hoge: moji 10
```

## 変数の扱い

* 型変換

```php
# print (5 + "5") error:pythonに暗黙的型変換はない
print (5 + int("5")) # 10
print (5 + float("5")) # 10.0
print (str(5) + "5") # 55
```

* 型表示

```php
// 型を知りたい場合はvar_dumpを利用する
var_dump(1); // int(1)
var_dump("h"); // string(1) "h"
var_dump([1,2]); // array(2) { [0]=> int(1) [1]=> int(2) }
```

* 配列の基本

```php
$array = [5, 5, 10]; # 配列php5.4以降
//$array = array(5,5,10) # それ以前

echo count($array); # 3
# 要素を直接参照しても型しかわからない
echo $array; # Array
var_dump($array); # array(3) { [0]=> int(5) [1]=> int(5) [2]=> int(10) }
# 配列 -> 文字列
$strObj = implode(",",$array);
echo $strObj; # 5,5,10
# 文字列 -> 配列
$array2 = split(",", $strObj);
var_dump($array2); # array(3) { [0]=> string(1) "5" [1]=> string(1) "5" [2]=> string(2) "10" }
# 要素の取得
echo $array[2]; # 10
$array[2] = 20;
var_dump($array); # array(3) { [0]=> int(5) [1]=> int(5) [2]=> int(20) }
# 要素確認
$isTwo = array_key_exists(2, $array);
var_dump($isTwo); # bool(true)  ※keyに2が存在するのでTRUE
$isTwo = in_array(2, $array);
var_dump($isTwo); # bool(false)  ※valueに2が存在するのでFALCE
```

* 配列の並び替え

```php
$array = array(80, 100, 30, 20);
var_dump($array); # array(4) { [0]=> int(80) [1]=> int(100) [2]=> int(30) [3]=> int(20) }
asort($array); #arrayを昇順にする
var_dump($array); # array(4) { [3]=> int(20) [2]=> int(30) [0]=> int(80) [1]=> int(100) } 
arsort($array); # arrayを降順にする
var_dump($array); # array(4) { [1]=> int(100) [0]=> int(80) [2]=> int(30) [3]=> int(20) }
```

分岐
-----------------------------

```php
$score = 50;
// if文
if ($score > 40){
	echo "ok1";
	echo "ok2";
}

// else if
if ($score > 60){
	echo "ng";
}elseif ($score > 55){
	echo "ng";
}else{
	echo "else ok";
}

// and複数条件(&&でもOK)
if (40 < $score and $score < 60){
	echo "ok3";
}

// or複数条件(||でもOK)
if ($score > 80 or $score < 70){
	echo "ok4";
}

// [表示]
// ok1ok2else okok3ok4

// PHPは比較演算子に「==」をもつが、「===」で型一致までの比較演算を行うことができる
// 型を含めた否定の場合は「!==」のようにうしろにイコールを追加する

// php ではjavaなどとことなり、
// 空文字、数値の0や配列の数が０のときや、nullのときにfalseと解釈される

```

* switch文

```php

$str = "hoge";
switch ($str) {
case "hoge": 
	echo "hoge";
	// breakをいれないと、以下がそのまま実行される
case "fuga": 
	echo "fuga";
	break;
case "piyo": 
	echo "piyo";
	break;
default: 
	echo "default";
}
// [画面表示]
// hogefuga
```


繰り返し
---------------------------

* for文（一定回数の繰り返し）

```php
for($i = 0; $i < 5 ; $i++){
	echo $i;
}
// [画面表示]
// 01234

```

* for文（リスト繰り返し:拡張for）

```php

$array = array(10, 20, 30, 40);
foreach($array as $data){
	if($data == 10){
		continue;// 戻る
	}
	if($data == 30){
		break; //if文から脱出
	}
	echo $data;
}

// [画面表示]
// 20
```


* for文（コロン構文）
    * htmlを直感的に書くことができる記法

```php

$array = array(10, 20, 30, 40);
// コロンからはじめて
foreach($array as $data):
	if($data == 10){
		continue;// 戻る
	}
	if($data == 30){
		break; //if文から脱出
	}
	echo $data;
// endforeachで終了がOK
endforeach;

// [画面表示]
// 20
```

* while文

```php
$i = 1;
while ($i < 5){
	echo $i;
	# phpはインクリメント（単項演算子）もOK
	$i += 1;
}
#[画面表示]
#1234
```

関数定義
----------------------

```php
#function 関数名(引数[ = 初期値]):
function increment($num = 1){
	return $num + 1
}

echo increment(); # 2(初期値)
echo increment(0); # 1(引数渡し)
```

クラス定義
------------------------

* javaなどでいうフィールドはpropertyという

```php
class User {
	# property
	public $name;

	# コンストラクタ
	public function __construct($name){
		$this->name = $name;
	}

	public function callName(){
		printf("user name : %s" , $this -> name);
	}
}

#インスタンス生成
$user1 = new User("hoge");
$user2 = new User("fuga");

# 処理実行
echo $user1->name; # hoge
$user1->callName(); # user name : hoge
$user2->callName(); # user name : fuga
```

* クラスの継承

```php
# 継承
class SuperUser{
	public $name;
	# インスタンス生成時に呼び出される変数
	public function __construct($name){
		$this->name = $name;
	}

	public function callName(){
		printf("SuperUser name : %s" ,$this->name);
	}

	# overloadはjavaのように実装できない
	// public function callName($name){
	// 	printf("SuperUser name : %s" ,$name);
	// }
}
class User extends SuperUser{
	# override可能
	public function callName(){
		printf("normalUser name : %s" ,$this->name);
	}
	public function callName2(){
		printf("name : %s" ,$this->name);
	}
}

$user3 = new User("piyo");
$user3->callName(); # normalUser name : piyo
$user3->callName2(); # name : piyo
$user3->callName("overload"); # normalUser name : piyo

```

* アクセス修飾子
 * public,protected,privateなどは、javaと同様に利用できる
 * finalもjavaのように利用できる
 * staticもjavaのように利用できる
 * 抽象クラスもabstractで利用可能
 * interfaceもjava同様（implementsでの継承方法も同じ）

```php
// staticメソッドは利用方法が異なる。
// 宣言は同じだが、呼び出し型は以下のようにコロン２つで呼び出す
User::staticMethod();
// static propery も宣言は同じだが、呼び出し型は同様に異なる
User::$staticProperty;
```

辞書式Mapオブジェクト（言語仕様として配列とMapは同じ）
---------------------------------------------

```php
$dict = array("taro" => 10, "jiro" => 20, "saburo" => 30);
# 表示
echo $dict; //Array
var_dump($dict); //array(3) { ["taro"]=> int(10) ["jiro"]=> int(20) ["saburo"]=> int(30) }

echo $dict["jiro"]; # 20

// 値の変更
$dict["jiro"] = 21;
echo $dict["jiro"]; # 21

/*
echo jiro" in $dict) #
# 一覧の取得
echo dict.keys()) #
echo dict.values()) #
echo dict.items()) #
*/
# 追加
$dict += array("siro" => 40,"goro" => 50);
// arrayMergeを使ってもOK
// $dict += array_merge($dict, array("siro" => 40,"goro" => 50));

var_dump($dict); #array(5) { ["taro"]=> int(10) ["jiro"]=> int(21) ["saburo"]=> int(30) ["siro"]=> int(40) ["goro"]=> int(50) }
```

* 辞書繰り返し（for文）

```php
$dict = array("taro" => 10, "jiro" => 20, "saburo" => 30);
foreach($dict as $key => $value){
	echo "$key:$value <br/>";
}
#taro:10
#jiro:20
#saburo:30
```

ファイルIO
----------------------

例外処理
----------------------

interface
----------------------

Thread処理
----------------------

