# グループ化
## 同じ値を持つ行をグループとしてまとめて、GROUP BYを使用してじょりを行うことができる。  

- ## グループ化
## 表1、表2の値の同じパターンがある場合、グループ化する。
```sql
SELECT 集計する列 FROM 表名 GROUP BY グループ化する列；
例）
SELECT id FROM ex1 GROUP BY ex2;
```

- ## グループ化に対する条件
## グループ化にはHAVINGを使用してグループ化した後のグループに対して条件による絞り込みを可能とする。
## WHEREとHAVINGを混合して使用できる。
```sql
/*HAVINGのみ*/
SELECT 集計する列 FROM 表名 GROUP BY グループ化する表名 HAVING 条件；
/*HAVING,WHEREの混合して*/
SELECT 集計する列 FROM 表名 WHRER 条件　/*グループ化する前に絞り込む*/
  GROUP BY グループ化する表名 HAVING 条件; /*グループ化後さらに絞り込む*/
```

- ## グループ化してからの並び替え
##グループ化した後に、並び替えを行うことができる。
## 文の終わりにORDER BY で並び替えができる。
```sql
/*昇順*/
SELECT 集計する列 FROM 表名 GROUP BY グループ化する表 ORDER BY ;
/*降順*/
SELECT 集計する列 FROM 表名 GROUP BY グループ化する表 ORDER BY DESC;

例）
/*昇順*/
SELECT name FROM ex1 GROUP BY ex2 ORDER BY;
/*降順*/
SELECT name FROM ex1 GROUP BY ex2 ORDER BY DESC;
```

