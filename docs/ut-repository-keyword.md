# キーワードリポジトリクラスの単体テスト

## 1.複数レコード取得メソッド
### 指定した雑誌が存在する場合
#### テストデータ
##### ファイル名
`/repository/keyword-1.sql`
##### 雑誌テーブル
|雑誌ID|雑誌名|号数|出版社|発行日|更新日付|
|:--|:--|:--|:--|:--|:--|
|1|テスト雑誌|テスト号数|||(CURRENT_TIMESTAMP)|
##### キーワードテーブル
|雑誌ID|単語|開始ページ|更新日付|
|:--|:--|:--|:--|
|1|テスト単語1-1|1|(CURRENT_TIMESTAMP)|
|1|テスト単語1-2|10|(CURRENT_TIMESTAMP)|
|1|□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■|999|(CURRENT_TIMESTAMP)|
#### テスト内容
|メソッド|引数|戻り値（期待値）|
|:--|:--|:--|
|複数レコード取得メソッド|1|下記参照|
##### 戻り値の期待値
- 件数：3

|単語|開始ページ|
|:--|:--|
|テスト単語1-1|1|
|テスト単語1-2|10|
|□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■|999|

### 指定した雑誌が存在しない場合
#### テストデータ
##### ファイル名
`/repository/keyword-1.sql`
##### 雑誌テーブル
|雑誌ID|雑誌名|号数|出版社|発行日|更新日付|
|:--|:--|:--|:--|:--|:--|
|1|テスト雑誌|テスト号数|||(CURRENT_TIMESTAMP)|
##### キーワードテーブル
|雑誌ID|単語|開始ページ|更新日付|
|:--|:--|:--|:--|
|1|テスト単語1-1|1|(CURRENT_TIMESTAMP)|
|1|テスト単語1-2|10|(CURRENT_TIMESTAMP)|
|1|□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■□□□□□□□□□■|999|(CURRENT_TIMESTAMP)|
#### テスト内容
|メソッド|引数|戻り値（期待値）|
|:--|:--|:--|
|複数レコード取得メソッド|2|下記参照|
##### 戻り値の期待値
- 件数 = 0

|単語|開始ページ|
|:--|:--|

## 2.削除メソッド
### 指定した雑誌が存在する場合
#### テストデータ
##### ファイル名
`/repository/keyword-2.sql`
##### 雑誌テーブル
|雑誌ID|雑誌名|号数|出版社|発行日|更新日付|
|:--|:--|:--|:--|:--|:--|
|1|テスト雑誌|テスト号数|||(CURRENT_TIMESTAMP)|
##### キーワードテーブル
|雑誌ID|単語|開始ページ|更新日付|
|:--|:--|:--|:--|
|1|テスト単語2-1|1|(CURRENT_TIMESTAMP)|
#### テスト内容
|メソッド|引数|戻り値（期待値）|
|:--|:--|:--|
|削除メソッド|1|1|
#### メソッド実行前後のレコード数の検証
|タイミング|期待値|
|:--|:--|
|実行前|1|
|実行後|0|

### 指定した雑誌が存在しない場合
#### テストデータ
##### ファイル名
`/repository/keyword-2.sql`
##### 雑誌テーブル
|雑誌ID|雑誌名|号数|出版社|発行日|更新日付|
|:--|:--|:--|:--|:--|:--|
|1|テスト雑誌|テスト号数|||(CURRENT_TIMESTAMP)|
##### キーワードテーブル
|雑誌ID|単語|開始ページ|更新日付|
|:--|:--|:--|:--|
|1|テスト単語2-1|1|(CURRENT_TIMESTAMP)|
#### テスト内容
|メソッド|引数|戻り値（期待値）|
|:--|:--|:--|
|削除メソッド|2|0|
#### メソッド実行前後のレコード数の検証
|タイミング|期待値|
|:--|:--|
|実行前|1|
|実行後|1|

## 3.登録メソッド
#### テストデータ
##### ファイル名
`/repository/keyword-3.sql`
##### 雑誌テーブル
|雑誌ID|雑誌名|号数|出版社|発行日|更新日付|
|:--|:--|:--|:--|:--|:--|
|1|テスト雑誌|テスト号数|||(CURRENT_TIMESTAMP)|
##### キーワードテーブル
|雑誌ID|単語|開始ページ|更新日付|
|:--|:--|:--|:--|
#### テスト内容
|メソッド|引数|戻り値（期待値）|
|:--|:--|:--|
|登録メソッド|下記参照|1|
##### 引数に渡すキーワードオブジェクト
|雑誌ID|単語|開始ページ|
|:--|:--|:--|
|1|テスト単語3-1|123|
#### メソッド実行前後のレコード数の検証
|タイミング|期待値|
|:--|:--|
|実行前|0|
|実行後|1|
#### メソッド実行後のテーブルの検証
|雑誌ID|単語|開始ページ|
|:--|:--|:--|
|1|テスト単語3-1|123|
