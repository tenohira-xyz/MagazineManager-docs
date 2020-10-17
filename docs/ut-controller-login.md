# ログイン画面コントローラクラスの単体テスト

## 非ログイン状態で初期表示
### 条件
- 匿名ユーザ
- `/login`にGETリクエストを送信する。

### 確認事項
1. HTTPステータスがOK(200)となることを確認する。
1. `login.html`をビューとして返すことを確認する。
1. 表示内容を確認する。

## 管理者権限で初期表示
### 条件
- 管理者ユーザ
- `/login`にGETリクエストを送信する。

### 確認事項
1. HTTPステータスがForbidden(403)となることを確認する。
