# 記事リポジトリクラス

## 複数レコード取得メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- 記事のリスト : `List<Article>`

### データベースアクセス
#### 取得項目
- 記事のリスト
    - セクション : `String`
    - タイトル : `String`
    - 開始ページ : `int`

#### 取得元テーブル
- 記事

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
SELECT section, title, start_page FROM article WHERE magazine_id = ?
```

## 削除メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- 削除したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- 記事

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
DELETE FROM article WHERE magazine_id = ?
```

## 登録メソッド
### 引数
- 記事オブジェクト : `Article`

### 戻り値
- 登録したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- 記事

#### 登録内容
- 雑誌ID = 引数.雑誌ID : `int`
- セクション = 引数.セクション : `String`
- タイトル = 引数.タイトル : `String`
- 開始ページ = 引数.開始ページ : `int`
- 更新日付 = 現在日時 : `Date`

#### SQL
```sql
INSERT INTO article(magazine_id, section, title, start_page, update_time) VALUES(?, ?, ?, ?, CURRENT_TIMESTAMP)
```

