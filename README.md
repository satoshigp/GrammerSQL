# SQL文の説明を記述する

- ## 表の作成  
```sql
 CREATE TABLE 表名 (列名1 データ型,列名2 データ型・・・);  
```
- ## 表構造の確認
```sql
  DESCRIBE 表名
  DESC 表名
```

- ## データの挿入  
```sql
  INSERT INTO 表名 VALUES(データ1,データ2・・・);
///例）INSERT INTO tb1 VALUES('E01','中村',40);
```
- ### 表データの表示
```
SELECT 例名1
```
- ## 内容の確定
```  
    COMMIT
```
- ## 変更前の状態に戻す
```
    ROLLBACK
```
- ## 表の構造の変更
  - ### 列の定義を変更する
```
 ALTER TABLE 表名 MODIFY(列名 データ型);
//例）ALTER TABLE tb1 MODIFY(name VARCHAR2(12));
```
- ### 列の追加
```
ALTER TABLE 表名 ADD(列名 データ型);
//例）ALTER TABLE tb1 ADD (entry DATE)
```
 - ### 列の削除
```
ALTER TABLE 表名 DROP(列名);
例）ALTER TABLE tb1 DROP (entry);
```
- ### 列名の変更
```
ALTER TABLE 表名 RENAME COLUMN ,元列名 TO 新列名;
例）ALTER TABLE tb1 RENAME COLUMN  col2 TO age;
```

- ### 表名の変更 
```
ALTER TABLE 表名 RENAME TO 新表名;
例）ALTER TABLE tb1 TO tb1_test;
```

# SELECT

- ## 別名の理由
```
 SELECT 列名 AS "別名" FROM 表名;
例）SELECT col3 AS "売上" FROM tb1_test;
//複数の場合は「，」カンマで区切る。
```
- ## 関数の利用

 - ### AVG関数
 1.平均値を返す
```
 SELECT AVG(col1) FROM tb1_test;
```
  - ### SUM関数
 1.合計値を返す
```
 SELECT SUM(col1) FROM tb1_test;
```
 - ### COUNT関数
 1.データ件数を返す
```
 SELECT AVG(col1) FROM tb1_test;
```
 - ### TO_CHAR関数
 1.DATE型やTIMESTAMP型のデータを指定した形式の文字列に変換する
```
SELECT TO_CHAR(SYSTTAMP , "yyyy-mm・・・");
```
  - ## 文字列の連結
```
SELECT 文字列1 ||  文字列2 ・・・; 
//例）SELECT col1 || col2 || 'さん' FROM tb1_test;
//「||」パイプを2つ並べで連結。
```

# WHEREをつかった抽出
 - ### 条件に一致する行だけをSELECTで表示する場合、 WHEREＷを用いる
| 演算子 | 意味 |
| ------------------------------ | ----------------------------------------- |
| a IN b | bのリストの中にaがあるかどうか |
| a NOT IN b | bのリストの中にaがないかどうか |
| a BETWEEN b AND c | aがb以上c以下に間にあるかどうか |
| a NOT BETWEEN b AND c | aがb以上c以下に間にないどうか |

- ## 等しいかどうかの判定
```
SELECT * FROM 表名_test WHERE 列名 = 値;
例）SELECT * FROM tb1_test WHERE col1 = '中村';　//文字列OK
例2）SELECT * FROM tb1_test WHERE col2 = 100 ; //数値OK
例3）SELECT * FROM tb1_test WHERE NOT col1 = '中村'; //否定
```
- ## LIKEによる曖昧検索
 - ### LIKE演算子を使うと、ぴったりな条件ではなく、一部のみ一致したデータを取り出すことができる
| 文字 | 意味 |
|:--|--:|
| % | 任意の長さ(ゼロを含む)の文字列 |
| _ | 任意の1文字 |
```
SELECT * FROM 表名 WHERE LIKE パターン;
SELECT 列名 FROM 表名 WHERE LIKE パターン;
例）SELECT * FROM 表名 WHERE LIKE '%中%';//中の前後に文字があれば抽出
例2）SELECT 列名 FROM 表名 WHERE LIKE '中%';//中の後に文字があれば抽出
例3）SELECT 列名 FROM 表名 WHERE NOT LIKE '中%';//中を含まないデータ抽出
```

- ## NULL を使った条件
 - ### NULLとは「何もない値、不明な値」を指す。データ挿入時、初期値をセットしなければNULLがはいる。
 - ### NULLかどうかを調べる際は「IS NULL」を使用する「=」では判定不可
```
SELECT * FROM 表名 WHERE 列名 IS NULL ;
例）SELECT * FROM tb1_test WHERE col2 IS NULL ;//NULLなら抽出
例2）SELECT * FROM tb1_test WHERE col2 IS NOT NULL ;//否定、 NULLでない列を抽出
```

- ## 重複データの扱い
 - ### DISTINCTで重複したデータを1回だけ表示するようにする。
```
SELECT DISTINCT 列名 FROM 表名;
例）SELECT DISTINCT col1 FROM tb1_test;
```

# 表や行のコピー
- ## 表のコピー
```
CREATE TABLE 新規の表名 AS SELECT * FROM 既存の表名;
例）CREATE TABLE tb2 AS SELECT * FROM tb1_test;
```
- ## 既存の表に他の表の行のコピー


```sql
INSERT INTO 表名 SELECT 列名 ・・・ FROM 既存の表;
INSERT INTO 表名 SELECT 列名 ・・・ FROM 既存の表 WHERE 条件;
//tb1_testのcol1データを全てコピー
例）INSERT INTO tb2 SELECT col1 FROM tb1_test;
//条件を満たしたtb1_testのcol1データをコピー
例2）INSERT INTO tb2 SELECT col1 FROM tb1_test WHERE col1>=100;
```


# ルール

 - ## 命名規約

 - ## データ型

