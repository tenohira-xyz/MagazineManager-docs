# 雑誌新規登録画面のコントローラ
- クラス名：`RegisterController`

## 初期表示
- リクエストメソッド：GET
- リクエストURL：`/register`
- 実行権限：管理者のみ

### 処理内容
1. [雑誌新規登録画面のView](screen-register.md#View名)を返す。

## 登録
- リクエストメソッド：POST
- リクエストURL：`/register/create`
- 実行権限：管理者のみ

### 処理内容
1. 入力チェックを行う。
    - エラーがある場合は[雑誌新規登録画面（当画面）のView](screen-register.md#View名)を返す。
1. フォームに入力された「雑誌名」と「号数」を[雑誌サービスクラスの存在チェックメソッド](service-magazine.md#存在チェックメソッド（雑誌名、号数）)に渡し、指定した雑誌情報が存在するかチェックする。
    - 存在する場合、[雑誌登録済例外](exception.md#雑誌登録済例外)を発生させる。発生した例外は[ハンドラメソッド](controller-register.md#雑誌登録済例外ハンドラ)で処理する。
1. 「雑誌名」と「号数」を[雑誌サービスクラスの登録メソッド](service-magazine.md#登録メソッド)に渡して、登録処理を実行する。
1. 登録処理の実行結果を比較する。
    - 成功した場合、[雑誌一覧画面のView](screen-magazinelist.md#View名)を返す。
    - 失敗した場合、[共通エラー画面のView]()を返す。

## 雑誌登録済例外ハンドラ
- 処理対象の例外：[雑誌登録済例外](exception.md#雑誌登録済例外)

### 処理内容
1. 画面に表示する[エラーメッセージ](exception.md#雑誌登録済例外)を定義する。
2. [共通エラー画面のView]()を返す。
