# 修正・削除
## 列データの更新、列、表のデータを削除するにはUPDATE,DELETEを使用する。

- ## 列データの更新
## 列データの削除を行う。WHEREで条件を指定することもできる。
## 削除したデータはROLLBACKで戻すことが可能
```sql
//条件なし
UPDATE 表名 SET 列名 = 値 ;
/*条件あり*/
UPDATE 表名 SET 列名 = 値 WHERE 条件;

例）
//条件なし
UPDATE ex1 SET name = '深田' ;
/*条件あり*/
UPDATE ex1 SET age = 20 WHERE age＜10;

```
---
- ## 行の削除
## 行の削除を行う。WHEREで条件を指定する事もできる。WHEREで条件を指定する事もできる。
## 削除した列はROOLBACKで元に戻すことが不可能
```sql
//条件なし
DELETE FROM 表名 列名;
/*条件あり*/
DELETE FROM 表名 WHERE 条件;

例）
/*条件なし*/
DELETE FROM ex1 name;
/*条件あり*/
DELETE FROM ex1 age WHERE name IS NULL;
```
---
- ## 全行の削除
## 全行の削除を行う。
## ＳＱＬはつりーじょうで管理されており、データを根元から切るのでROLLBACKは不可能
```sql
TRUNCATE TABLE 表名
//例）
TRUNCATE TABLE ex1;
```
---
- ## 表の削除
## 表の削除を行う。UPDATEを使用する。
## 削除されたデータはROLLBACKで元に戻すのは不可能　
```sql
DROP TABLE 表名;
例）
DROP TABLE ex1;
/*条件あり*/
```



