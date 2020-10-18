# ログイン画面の結合テスト

## ログイン（失敗：未認証ユーザ）
### 事前条件
- ユーザに管理者権限がないこと。

### テスト内容
1. `/login`にアクセスして、画面を表示する。
1. フォームに下記の内容を入力して、「ログイン」ボタンを押す。
    - ユーザ名：`user`
    - パスワード：`user`
1. ログインエラーメッセージが画面に表示されることを確認する。

## ログイン（成功：未認証ユーザ）
### 事前条件
- ユーザに管理者権限がないこと。

### テスト内容
1. `/login`にアクセスして、画面を表示する。
1. フォームに下記の内容を入力して、「ログイン」ボタンを押す。
    - ユーザ名：`admin`
    - パスワード：`password`
1. 雑誌一覧画面に遷移することを確認する。
    - `/list`に遷移すること。
1. 管理者ユーザであることを確認する。
    - 管理者権限の画面レイアウトで表示されていること。

## ログイン（アクセス不可：管理者ユーザ）
### 事前条件
- 管理者ユーザであること。

### テスト内容
1. `/login`にアクセスして、アクセス拒否されることを確認する。
    - ブラウザのアドレスバーに直接URLを入力してアクセスする。
