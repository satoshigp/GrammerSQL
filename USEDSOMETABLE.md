# 複数の表の利用
## 2つ以上の表からデータを組み合わせて、必要なデータを取得する

- ## 関係演算
##3 今度表を入れます。。。。。。

- ## 集合演算
### 集合演算は、二つ以上テーブルから集合の考え方を利用して、データを取り出す演算子。
### 集合演算子
### [図でイメージするOracle DatabaseのSQL全集 第2回 集合演算など](https://www.oracle.com/technetwork/jp/articles/otnj-sql-image2-308626-ja.html)
|集合|演算子|意味|
|---|---|---|
|和集合|UNION|和集合、重複を除いた集合|
|和集合|UNION ALL|和集合、重複を合わせた集合|
|和集合|INTERSECT|積集合、共通部分の集合|
|和集合|MINUS|差集合、非共通部分の集合|

- ## 和集合
### 和集合を行うには、UNION , UNION ALL　を使用する。
### WHEREで条件を指定する事ができる。
```sql
/*UNION:重複を含まない*/
SELECT 列名 FROM 表名 UNION FROM 表名2;
/*UNION ALL ： 重複を含めない*/
SELECT 列名 FROM 表名 UNION ALL FROM 表名2;

例）
/*UNION*/  
SELECT id FROM ex1 UNION FROM ex2;
/*UNION ALL*/
SELECT id FROM ex1 UNION ALL FROM ex2;
```
- ## 積集合
### 積集合を行うには INTERSECT を使用する。
```sql
/*INTERSECT*/  
SELECT 列名 FROM 表名1 INTERSECT FROM 表名2;

例）
SELECT id FROM ex1 INTERSECT FROM ex2;

```
- ## 差集合
### 差集合を行うには、MINUS を使用する。
```sql
*MINUS*/  
SELECT 列名 FROM 表名1 MINUS FROM 表名2;

例）
SELECT id FROM ex1 MINUS FROM ex2;

```

- ## 結合
### 複数の表を何らかのキーで処理することを結合という。

- ## 内部結合
### データ単体を取り出す。


```sql
SELECT 列名 FROM 表名1 JOIN 表名2 ON 表名1.id=表名2.id(条件);
/*表名に別名を使用することも可能*/
SELECT 列名 FROM 表名1 X.id,Y.name JOIN 表名2 Y ON 表名1.id=表名2.id(条件);

例)
SELECT ex1.id,ex2.name FROM ex1 JOIN ex2 ON ex1.id=ex2.id;
/*別名を使用して*/
SELECT X.id,Y.name FROM ex1 X JOIN ex2 Y ON ex1.id=ex2.id;
```

- ## USINGの使用
### JOIN ON　のON~を使用せず、お互いの表の参照する列名が同じならば、USING(共通の列名)でまとめて判定が可能
```sql
SELECT 列名 FROM 表名1 JOIN 表名2 USING(共通の列名);
例）
SELECT id FROM ex1 JOIN ex2 USING(id);
/*idに[表名.]は不要*/

```

- ## 外部結合
### すべての行を取り出す 
```sql
/*左外部結合
SELECT 列名 FROM 表名1 LEFT JOIN 表名2 ONやUSINGによる条件;
/*右外部結合*/
SELECT 列名 FROM 表名2 RIGTH JOIN 表名1 ONやUSINGによる条件;

例）
/*左外部結合
SELECT id FROM ex1 LEFT JOIN 表名2 ON ex1.id=ex2.id;
/*右外部結合*/
SELECT id FROM ex2 RIGHT JOIN ex1 USING(id);
```

