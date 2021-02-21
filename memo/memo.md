# 二次元データ構造

　二次元データ構造を作る。

## 既存のデータ構造

データ構造|次元|key-type|順序保持|
----------|----|--------|--------|
Array|1|int|配列|あり。index順
Map|1|string|Key,Valueセット|あり。挿入順
Set|1|-|一意の値を格納できる|なし
Object|1|string|なし

## 二次元データソース

* ファイル
    * TSV,CSV
    * JSON,XML
    * YAML
    * TOML
    * INI
* プリミティブ
    * JSON,Object,Array,Set,Map

## TSV例

### 1Table-1File

#### Row

```tsv

行1列1  行1列2  行1列3
行2列1  行2列2  行2列3
```

#### Column+Row

##### Column min + Row

* 1行目：Column（Mapキー）
* 2行目以降：Row

```tsv
id  name
0   Yamada
1   Suzuki
```

##### Column main + Row

* 1〜3行目：Column
    * 1行目：key：Mapキー
    * 2行目：name：HTML表示名
    * 3行目：type：列の型
* 4行目以降：Row

```tsv
id  name
ID  名前
int str
0   Yamada
1   Suzuki
```

##### Column option + Row

　Columnが可変である。

* Columnがない
* Columnがある
    * 順序（何行目が何の項目か）

###### Column1列目にラベルあり

```tsv
key:id  name
name:ID 名前
type:int    str
0   Yamada
1   Suzuki
```

###### 1行目がColumn順序指定である

```tsv
key name    type
id  name
ID  名前
int str
0   Yamada
1   Suzuki
```

### 1Table-2File

* column.tsv
* row.tsv

　さらに以下のような設定ファイルもある。

* sort.tsv
* filter.tsv
* pagination.tsv
* autopager.tsv
* aggregate.tsv

#### column.tsv

* 1行目がヘッダ（列位置がどの項目か）

```tsv
key     name    type
id      ID      int
name    名前    str
```

#### row.tsv

```tsv
column: ./column.tsv
filter: ./filter.tsv
pagination: ./pagination.tsv
autopager: ./autopager.tsv
aggregate: ./aggregate.tsv
0   Yamada
1   Suzuki
```

　メタ情報は省略できるべき。

* 同じ階層にある
* 同じファイル名に特定のサフィックスがある
    * `0-column.tsv`
    * `0-row.tsv`
    * `0-sort.tsv`
    * `0-filter.tsv`
    * `0-pagination.tsv`
    * `0-autopager.tsv`
    * `0-aggregate.tsv`

　上記には問題がある。

* JSはファイルシステムを使えない
    * ファイル参照できない
        * `fetch` APIを使うしかない
            * ファイルが存在しないとき例外が出る
                * 遅延する
    * シンボリックリンクが使えない
        * 同じ`column`を流用するときなどでデータ重複が生じてしまう

##### Column max + Row

```tsv
1行目：key：Mapキー
2行目：name：HTML表示名
3行目：type：列の型
```

## 型

* Table
    * Column
    * Row

## テーブルデータ

データ種別|型
----------|--
table|Class
column(カラム。列)|Map
row(ロウ。行)|二次元配列

## メソッド

* 読込
    * `new Table()`
    * `new Table(objectArray)`
    * `new Table(columns)`
    * `Table.fromFile()`
* 書込
* 位置変更
    * 入替
        * 列
        * 行
    * ソート

