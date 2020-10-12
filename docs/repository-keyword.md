# キーワードリポジトリクラス

## 複数レコード取得メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- キーワードのリスト : `List<Keyword>`

### データベースアクセス
#### 取得項目
- キーワードのリスト
    - 単語 : `String`
    - 開始ページ : `int`

#### 取得元テーブル
- キーワード

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
SELECT word, start_page FROM keyword WHERE magazine_id = ?
```

## 削除メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- 削除したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- キーワード

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
DELETE FROM keyword WHERE magazine_id = ?
```

## 登録メソッド
### 引数
- キーワードオブジェクト : `Keyword`

### 戻り値
- 登録したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- キーワード

#### 登録内容
- キーワードオブジェクト
    - 雑誌ID = 引数.雑誌ID : `int`
    - 単語 = 引数.単語 : `String`
    - 開始ページ = 引数.開始ページ : `int`
    - 更新日付 = 現在日時 : `Date`

#### SQL
```sql
INSERT INTO keyword(magazine_id, word, start_page, update_time) VALUES(?, ?, ?, CURRENT_TIMESTAMP)
```

