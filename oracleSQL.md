## hello world

```sql
SELECT
	'hello world'
FROM
	DUAL
;
```

## コメントアウト

```sql
-- 一行コメント
/*
	複数行コメント
*/
```

順次（表示・型・配列）
------------------

## 標準出力

```sql
SELECT
	'moji' AS STR
FROM
	DUAL
;
```

* 文字列操作

```sql
SELECT
	'hohoge!!' AS STR1
,	length('hohoge!!') AS STR2
,	substr('hohoge!!',0) AS STR3
,	substr('hohoge!!',2,5) as STR4
,	substr('hohoge!!',2,length('hohoge!!') -3) AS STR5
FROM
	DUAL
;
```

* format表示
	* TODO

```sql
SELECT
	TO_CHAR()
FROM
	DUAL
;
```
