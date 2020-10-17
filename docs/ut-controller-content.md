# 目次画面コントローラクラスの単体テスト

## 非ログイン状態で初期表示（雑誌が存在する、リスト0件）
### 条件
- 匿名ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|複数レコード取得メソッド|1|0件（空のリスト）|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    ||||
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|1|

## 非ログイン状態で初期表示（雑誌が存在する、リスト1件以上）
### 条件
- 匿名ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|複数レコード取得メソッド|1|1件|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|123|
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|1|

## 非ログイン状態で初期表示（雑誌が存在しない）
### 条件
- 匿名ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|false|
1. HTTPステータスがOK(200)となることを確認する。
1. モデルに登録したパラメータにエラーメッセージが含まれているか検証する。
|名前|内容|
|:--|:--|
|status|500|
|error|エラー|
|message|指定した雑誌が存在しません。|
1. `error.html`をビューとして返すことを確認する。
1. 発生した例外が[雑誌非存在例外](exception.md#雑誌非存在例外)かを検証する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|0|

## 非ログイン状態で削除
### 条件
- 匿名ユーザ
- `/contents/1/edit`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|remove|1|

### 確認事項
1. HTTPステータスがForbidden(403)となることを確認する。

## 非ログイン状態で追加
### 条件
- 匿名ユーザ
- `/contents/1/edit`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|add||

### 確認事項
1. HTTPステータスがForbidden(403)となることを確認する。

## 非ログイン状態で登録
### 条件
- 匿名ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。

### 確認事項
1. HTTPステータスがForbidden(403)となることを確認する。

## 管理者権限で初期表示（雑誌が存在する、リスト0件）
### 条件
- 管理者ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|複数レコード取得メソッド|1|0件（空のリスト）|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    ||||
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|1|

## 管理者権限で初期表示（雑誌が存在する、リスト1件以上）
### 条件
- 管理者ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|複数レコード取得メソッド|1|1件|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|123|
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|1|

## 管理者権限で初期表示（雑誌が存在しない）
### 条件
- 管理者ユーザ
- `/contents/1`にGETリクエストを送信する。

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|false|
1. HTTPステータスがOK(200)となることを確認する。
1. モデルに登録したパラメータにエラーメッセージが含まれているか検証する。
|名前|内容|
|:--|:--|
|status|500|
|error|エラー|
|message|指定した雑誌が存在しません。|
1. `error.html`をビューとして返すことを確認する。
1. 発生した例外が[雑誌非存在例外](exception.md#雑誌非存在例外)かを検証する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|複数レコード取得メソッド|0|

## 管理者権限で削除
### 条件
- 管理者ユーザ
- `/contents/1/edit`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|セクション１|
|articleList[0].title|タイトル１|
|articleList[0].startPage|10|
|articleList[1].section|セクション２|
|articleList[1].title|タイトル２|
|articleList[1].startPage|20|
|remove|1|

### 確認事項
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。

## 管理者権限で追加
### 条件
- 管理者ユーザ
- `/contents/1/edit`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|セクション１|
|articleList[0].title|タイトル１|
|articleList[0].startPage|10|
|add||

### 確認事項
1. HTTPステータスがOK(200)となることを確認する。
1. `contentsList.html`をビューとして返すことを確認する。
1. 表示内容を確認する。

## 入力チェック（必須入力）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section||
|articleList[0].title||
|articleList[0].startPage||

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    ||||
1. `contentsList.html`をビューとして返すことを確認する。
1. エラーメッセージ数が2であることを確認する。
1. 想定通りのエラーメッセージが出力されていることを確認する。
    - セクションまたはタイトルが入力されていません。
    - 開始ページが入力されていません。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|

## 入力チェック（相関チェック、セクションのみ入力）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title||
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション||123|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（相関チェック、タイトルのみ入力）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section||
|articleList[0].title|テストタイトル|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    ||テストタイトル|123|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（文字列長：1文字）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|□|
|articleList[0].title|□|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |□|□|123|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（文字列長：最大数）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③|
|articleList[0].title|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□□□□□□□□□④□□□□□□□□□⑤|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□□□□□□□□□④□□□□□□□□□⑤|123|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（文字列長：超過）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□|
|articleList[0].title|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□□□□□□□□□④□□□□□□□□□⑤□|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□|□□□□□□□□□①□□□□□□□□□②□□□□□□□□□③□□□□□□□□□④□□□□□□□□□⑤□|123|
1. `contentsList.html`をビューとして返すことを確認する。
1. エラーメッセージ数が2であることを確認する。
1. 想定通りのエラーメッセージが出力されていることを確認する。
    - セクションは30文字以内で入力してください。
    - タイトルは50文字以内で入力してください。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|

## 入力チェック（数値型か）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|abc|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|abc|
1. `contentsList.html`をビューとして返すことを確認する。
1. エラーメッセージ数が1であることを確認する。
1. 想定通りのエラーメッセージが出力されていることを確認する。
    - 開始ページは数値を入力してください。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|

## 入力チェック（数値：-1）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|-1|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|-1|
1. `contentsList.html`をビューとして返すことを確認する。
1. エラーメッセージ数が1であることを確認する。
1. 想定通りのエラーメッセージが出力されていることを確認する。
    - 開始ページには0以上の数値を入力してください。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|

## 入力チェック（数値：0）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|0|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|0|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（数値：999）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|999|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|999|
1. `error.html`をビューとして返すことを確認する。
1. エラーメッセージ数が0であることを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 入力チェック（数値：1000）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|1000|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|1000|
1. `contentsList.html`をビューとして返すことを確認する。
1. エラーメッセージ数が1であることを確認する。
1. 想定通りのエラーメッセージが出力されていることを確認する。
    - 開始ページには999以下の数値を入力してください。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|

## 管理者権限で登録（成功）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|true|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|123|
1. HTTPステータスがFound(302)となることを確認する。
1. `magazineList.html`をビューとして返すことを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 管理者権限で登録（失敗）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|true|
|記事サービスクラス|更新メソッド|1, 記事リスト|false|
    - 記事リストの内容
    |セクション|タイトル|開始ページ|
    |:--|:--|:--|
    |テストセクション|テストタイトル|123|
1. HTTPステータスがOK(200)となることを確認する。
1. `error.html`をビューとして返すことを確認する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|1|

## 管理者権限で登録（例外）
### 条件
- 管理者ユーザ
- `/contents/1/update`にPOSTリクエストを送信する。
|パラメータ名|値|
|:--|:--|
|magazineId|1|
|articleList[0].section|テストセクション|
|articleList[0].title|テストタイトル|
|articleList[0].startPage|123|

### 確認事項
1. サービス層のモックを作成する。
|クラス|メソッド|引数|戻り値|
|:--|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|false|
1. HTTPステータスがOK(200)となることを確認する。
1. モデルに登録したパラメータにエラーメッセージが含まれているか検証する。
|名前|内容|
|:--|:--|
|status|500|
|error|エラー|
|message|指定した雑誌が存在しません。|
1. `error.html`をビューとして返すことを確認する。
1. 発生した例外が[雑誌非存在例外](exception.md#雑誌非存在例外)かを検証する。
1. サービス層のメソッドの呼び出しを検証する。
|クラス|メソッド|呼び出し回数|
|:--|:--|:--|
|雑誌サービスクラス|存在チェックメソッド（雑誌ID）|1|
|記事サービスクラス|更新メソッド|0|
