# tsv2array

　TSV文字列データからarray,object,MapといったJSオブジェクト型に変換する。

## 変換パターン

入力|出力
----|----
TSV文字列|二次元配列、オブジェクト配列、Map
二次元配列|TSV文字列、オブジェクト配列、Map
オブジェクト配列|TSV文字列、二次元配列、Map
Map|TSV文字列、二次元配列、オブジェクト配列

## API

* Tsv
    * `new Tsv(source)`
    * `Tsv.toArray(source)`
    * `Tsv.toObject(source)`
    * `Tsv.toMap(source)`
    * `Tsv.toTsv(source)`

