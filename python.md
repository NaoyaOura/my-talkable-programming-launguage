hello world
--------------------------

```py3
if __name__ == '__main__':
	print("Hello Wold")
```




## コメントアウト

```py3:コメントアウト
# 単一コメント
# 複数行のコメントアウト存在しない

"""
複数行コメントの代わりとなる方法として、
ダブルクォートかシングルクォートを利用することができるが、
インデントがずれていると利用できなかったりと
問題が起こりやすい
"""
```

順次（表示・型・配列）
---------------------------


```py3:文字コードの指定（ファイルの文頭に下記コメントをつける）
# coding: UTF-8
```

## 標準出力

```py3
print("moji") # mojiと表示される
print "moji" # python2系の書き方で、この書き方だと3系はエラーになる
print(u"日本語") # 日本語を利用するときは、uを先頭につける
```

* 変数

```py3
# 変数宣言は不要
hoge = "hoge"
```

* 文字列操作

```py3
str = "hohoge!!" # 文字列定義
print(str) # hogege!!と表示される
print(len(str)) # 8と表示（文字列の長さが表示）
print(str[0:]) # hohoge!!と表示(indexの0番目から最終行まで取得)
print(str[2:7]) # hoge!と表示（indexの2番目から7-1(=6)番目までのhoge!と表示される）
print(str[2:-1]) # hoge!と表示（indexの2番目から後ろから-1-1(=-2)番目までのhoge!と表示される）
```

* format表示

```py3
print("hoge: %d"    % 10)     # hoge: 10
print("hoge: %10d"  % 10)     # hoge:         10
print("hoge: %010d" % 10)     # hoge: 0000000010
print("hoge: %f"    % 10.123) # hoge: 10.123000
print("hoge: %.2f"  % 10.123) # hoge: 10.12
print("hoge: %s"    % "moji") # hoge: moji
print("hoge: %s %d" % ("moji", 10)) # hoge: moji 10
```

## 変数の扱い

* 型変換

```py3
# print (5 + "5") error:pythonに暗黙的型変換はない
print (5 + int("5")) # 10
print (5 + float("5")) # 10.0
print (str(5) + "5") # 55
```

* 型表示

```py3
print(type(1)) #<class 'int'>
print(type("h")) #<class 'str'>
print(type([1,2])) #<class 'list'>
print(isinstance(1,int)) # True
print(isinstance(1,list)) # False
```

* 配列の基本

```py3
array = [5, 5, 10] # 配列
print(len(array)) # 配列の長さを求める3
# 要素を直接参照しても値はわかる
print(array) # [5, 5, 10]
# 配列 -> 文字列
# 配列の型が文字列なら",".join(array)でOK
strObj = ",".join([str(t) for t in array])
print(strObj)
# 文字列 -> 配列
array2 = strObj.split(",")
print(array2)
# 要素の取得
print(array[2]) # 10
array[2] = 20
print(array) # [5, 5, 20]
print(array[0:2]) # [5,5] ※index0番目から2-1(=1)番目の数の配列を取得
# 要素確認
isTwo = 2 in array # 配列に2があるか
print(isTwo) # False（2がないため）
```

* 配列の並び替え

```py3
array = [80, 100, 30, 20]
array.reverse() #arrayを逆順にする
print(array) # [20, 30, 100, 80]
array.sort() # 小さい順に並べる
print(array) # [20, 30, 80, 100]
```

分岐
-----------------------------

```py3
score = 50
# if文
if score > 40:
	print("ok1")
	print("ok2")

# ifはインデントが命
if score > 60:
	print("ng")
print("ok3")

# else if
if score > 60:
	print("ng")
elif score > 55:
	print("ng")
else:
	print("else ok")

# and複数条件
if 40 < score and score < 60:
	print("ok4")

# and複数条件2
if 40 < score < 60:
	print("ok5")

# or複数条件
if score > 80 or score < 70:
	print("ok6")

# [コンソール]
# ok1
# ok2
# ok3
# else ok
# ok4
# ok5
# ok6
```

* switch文は存在しない

繰り返し
---------------------------

* for文（一定回数の繰り返し）

```py3
for i in range(0, 5):
	print(i)
# [コンソール]
# 0
# 1
# 2
# 3
# 4
```

* for文（リスト繰り返し:拡張for）

```py3
array = [10, 20, 30, 40]
for data in array:
	if data == 10:
		continue # 戻る
	if data == 30:
		break # if文から脱出
	print(data)

# [コンソール]
# 20
```

* while文

```py3
i = 1
while i < 5:
	print(i)
	# pythonはインクリメント不可
	i += 1
#[コンソール]
#1
#2
#3
#4
```

関数定義
----------------------

```py3
#def 関数名(引数[ = 初期値]):
def increment(num = 1):
	return num + 1

print(increment()) # 2(初期値)
print(increment(0)) # 1(引数渡し)
```

```py3:配列に対するメソッドと無名関数
# map:配列に対するメソッドの適応
print(list(map(increment,[10,11,12]))) # [11, 12, 13]

# 無名関数
print(list(map(lambda num:num + 1, [10,11,12])))# [11, 12, 13]
```

クラス定義
------------------------

```py3
class User():
	# __init__はインスタンス生成時に実行
	def __init__(self, name):
		self.name = name

	def callName(self):
		print("user name : %s" %self.name)

#インスタンス生成
user1 = User("hoge")
user2 = User("fuga")

# 処理実行
print(user1.name) # hoge
user1.callName() # user name : hoge
user2.callName() # user name : fuga
```

* クラスの継承

```py3
# 継承
class SuperUser():
	# インスタンス生成時に呼び出される変数
	def __init__(self, _name):
		self.name = _name

	def callName(self):
		print("SuperUser name : %s" %self.name)

	# overloadはpythonではできない
	#def callName(self, hoge)
	#	print("")

class User(SuperUser):
	# override可能
	def callName(self):
		print("normalUser name : %s" %self.name)
	def callName2(self):
		print("name : %s" %self.name)


user3 = User("piyo")
user3.callName() # normalUser name : piyo
user3.callName2() # name : piyo
```


配列以外のListオブジェクト（言語仕様）
--------------------

```py3:tuple（要素が変更できない配列）
foo = (10, 20, 30)
print(foo) # (10, 20, 30)
foo2 = list(foo) # tuple -> list変換
print(foo2)　# [10, 20, 30]
foo3 = tuple(foo2) # list -> tuple変換
print(foo3) # (10, 20, 30)
```

集合型Setオブジェクト（言語仕様）
--------------------

```py3
x = set([1, 1, 1, 2, 2, 3])
print(x) # {1, 2, 3}

# 集合型の特性
a = set([1, 2, 3, 4])
b = set([3, 4, 5])
# 和集合
print(a | b) #{1, 2, 3, 4, 5}
# 差集合
print(a - b) #{1, 2}
# 積集合
print(a & b) #{3, 4}
# いずれにも属さないもの
print(a ^ b) #{1, 2, 5}
```

辞書式Mapオブジェクト（言語仕様）
----------------------------

```py3
dict = {"taro":10, "jiro":20, "saburo":30}
# 表示
print(dict)
print(dict["jiro"]) # 20
print("jiro" in dict) # True(jiroが存在するため)
# 一覧の取得
print(dict.keys()) # dict_keys(['saburo', 'jiro', 'taro'])
print(dict.values()) # dict_values([30, 20, 10])
print(dict.items()) # dict_items([('saburo', 30), ('jiro', 20), ('taro', 10)])
# 追加
dict.update({"siro":40,"goro":50})
print(dict) #{'taro': 10, 'siro': 40, 'goro': 50, 'jiro': 20, 'saburo': 30}
```

```py3:辞書繰り返し（for文）
dict = {"taro":10, "jiro":20, "saburo":30}

for key,val in dict.items(): # python2系だと dict.iteritems()
	print("%s:%d" % (key,val))
#[コンソール]
#jiro:20
#saburo:30
#taro:10

for key in dict.keys(): # python2系だと dict.iterkeys()
	print(key)
#[コンソール]
#jiro
#saburo
#taro

for val in dict.values(): # python2系だと dict.itervalues()
	print(val)
#[コンソール]
#30
#10
#20
```

ファイルIO
----------------------

例外処理
----------------------

interface
----------------------

Thread処理
----------------------

