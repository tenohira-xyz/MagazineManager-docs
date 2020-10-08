# 索引画面のコントローラ
- クラス名：`IndexListController`

## 初期表示
- リクエストメソッド：GET
- リクエストURL：`/index/{雑誌ID}`
- 実行権限：全て

### 処理内容
1. 「雑誌ID」を[雑誌サービスクラスの存在チェックメソッド]()に渡し、指定した雑誌情報が存在するかチェックする。
    - 存在しない場合、雑誌非存在例外を発生させる。発生した例外は[ハンドラメソッド](controller-index.md#雑誌非存在例外ハンドラ)で処理する。
1. 「雑誌ID」を[キーワードサービスクラスの複数レコード取得メソッド]()に渡し、指定した雑誌のキーワードのリストを取得する。
1. 取得した情報を索引画面のフォームに詰める。
1. [索引画面のView](screen-index.md#View名)を返す。

## 一覧の入力欄を1行削除
- リクエストメソッド：POST
- リクエストURL：`/index/{雑誌ID}/edit`
- パラメータ：`remove`
- 実行権限：管理者権限

### 処理内容
1. キーワードオブジェクトのリストから指定した位置にあるオブジェクトを削除する。
1. [索引画面のView](screen-index.md#View名)を返す。

## 一覧の入力欄を1行追加
- リクエストメソッド：POST
- リクエストURL：`/index/{雑誌ID}/edit`
- パラメータ：`add`
- 実行権限：管理者権限

### 処理内容
1. キーワードオブジェクトのリストの一番下にオブジェクトを追加する。
1. [索引画面のView](screen-index.md#View名)を返す。

## 登録処理
- リクエストメソッド：POST
- リクエストURL：`/index/{雑誌ID}/update`
- 実行権限：管理者権限

### 処理内容
1. 「雑誌ID」を[雑誌サービスクラスの存在チェックメソッド]()に渡し、指定した雑誌情報が存在するかチェックする。
    - 存在しない場合、雑誌非存在例外を発生させる。発生した例外は[ハンドラメソッド](controller-index.md#雑誌非存在例外ハンドラ)で処理する。
1. 入力チェックを行う。
    - エラーがある場合は[索引画面（当画面）のView](screen-index.md#View名)を返す。
1. 複数の「雑誌ID」「キーワード」「開始ページ」を[キーワードサービスクラスの更新メソッド]()に渡して、更新処理を実行する。
1. 更新処理の実行結果を比較する。
    - 成功した場合、[雑誌一覧画面のView](screen-magazinelist.md#View名)を返す。
    - 失敗した場合、[共通エラー画面のView]()を返す。

## 雑誌非存在例外ハンドラ
- 処理対象の例外：`MagazineNotExistException`

### 処理内容
1. 画面に表示する[エラーメッセージ]()を定義する。
1. [共通エラー画面のView]()を返す。
