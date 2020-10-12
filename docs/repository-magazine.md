# 雑誌リポジトリクラス

## 存在チェックメソッド（雑誌ID）
### 引数
- 雑誌ID : `int`

### 戻り値
- レコード数 : `int`

### データベースアクセス
#### 取得項目
- レコード数（雑誌ID）: `int`

#### 取得元テーブル
- 雑誌

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
SELECT count(magazine_id) FROM magazine WHERE magazine_id = ?
```

## 存在チェックメソッド（雑誌名、号数）
### 引数
- 雑誌名 : `String`
- 号数 : `String`

### 戻り値
- レコード数 : `int`

### データベースアクセス
#### 取得項目
- レコード数（雑誌ID） : `int`

#### 取得元テーブル
- 雑誌

#### 条件
- 雑誌名 = 引数.雑誌名 : `String`
- 号数 = 引数.号数 : `int`

#### SQL
```sql
SELECT count(magazine_id) FROM magazine WHERE name = ? AND number = ?
```

## 単一レコード取得メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- 雑誌オブジェクト : `Magazine`

### データベースアクセス
#### 取得項目
- 雑誌クラス
    - 雑誌名
    - 号数
    - 出版社
    - 発行日

#### 取得元テーブル
- 雑誌

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
SELECT name, number, publisher, issue_date FROM magazine WHERE magazine_id = ?
```

## 複数レコード取得メソッド
### 引数
なし

### 戻り値
- 雑誌のリスト : `List<Magazine>`

### データベースアクセス
#### 取得項目
- 雑誌クラスのリスト
    - 雑誌ID : `int`
    - 雑誌名 : `String`
    - 号数 : `String`

#### 取得元テーブル
- 雑誌

#### 条件
なし

#### SQL
```sql
SELECT magazine_id, name, number FROM magazine
```

## 削除メソッド
### 引数
- 雑誌ID : `int`

### 戻り値
- 削除したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- 雑誌

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### SQL
```sql
DELETE FROM magazine WHERE magazine_id = ?
```

## 登録メソッド
### 引数
- 雑誌オブジェクト : `Magazine`

### 戻り値
- 登録したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- 雑誌

#### 登録内容
- 雑誌名 = 引数.雑誌名 : `String`
- 号数 = 引数.号数 : `String`
- 更新日付 = 現在日時 : `Date`

#### SQL
```sql
INSERT INTO magazine(name, number, update_time) VALUES(?, ?, CURRENT_TIMESTAMP)
```

## 更新メソッド
### 引数
- 雑誌オブジェクト : `Magazine`

### 戻り値
- 更新したレコード数 : `int`

### データベースアクセス
#### 操作テーブル
- 雑誌

#### 条件
- 雑誌ID = 引数.雑誌ID : `int`

#### 登録内容
- 雑誌名 = 引数.雑誌名 : `String`
- 号数 = 引数.号数 : `String`
- 出版社 = 引数.出版社 : `String`
- 発行日 = 引数.発行日 : `Date`
- 更新日付 = 現在日時 : `Date`

#### SQL
```sql
UPDATE magazine SET name = ?, number = ?, publisher = ?, issue_date = ?, update_time = CURRENT_TIMESTAMP WHERE magazine_id = ?
```
