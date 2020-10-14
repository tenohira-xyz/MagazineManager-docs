# セキュリティ設定クラス

## クラス名
`SecurityConfig`

## アクセス制御
### 匿名ユーザがアクセス可能なURL
- `/`：トップ画面（雑誌一覧画面）
- `/login`：ログイン画面
- `/list`：雑誌一覧画面
- `/detail/*`：雑誌詳細画面
- `/contents/*`：目次画面
- `/index/*`：索引画面

### 認証が必要なURL
- `/register`：雑誌新規登録画面

## ログイン（初期表示）
### ログイン画面のURL
`/login`
### 入力欄の名称
#### ユーザ名
`userName`
#### パスワード
`password`

## ログイン処理
### ログイン処理のURL
`/login`
### ログイン失敗時の遷移先URL
`/login`
### ログイン成功時の遷移先URL
`/list`

### ユーザ名とパスワードを取得するSQL
#### 取得項目
- ユーザ名
- パスワード
- 使用可否（一律`true`を設定する）

#### 取得元テーブル
- ユーザマスタ

#### 条件
- ユーザ名 = 入力フォームのユーザ名

#### SQL
```sql
SELECT name, password, true FROM m_user WHERE name = ?
```

### ユーザのロールを取得するSQL
#### 取得項目
- ユーザ名
- 権限

#### 取得元テーブル
- ユーザマスタ

#### 条件
- ユーザID = 入力フォームのユーザID

#### SQL
```sql
SELECT name, authority FROM m_user WHERE name = ?
```

## ログアウト
### ログアウト処理のURL
`/logout`
### ログアウト後の遷移先URL
`/list`

