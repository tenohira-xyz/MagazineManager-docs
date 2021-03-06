# 雑誌新規登録画面

## View名
`register.html`

## 画面の表示権限
管理者のみ

## 基準URL
`/register`

## 画面表示項目
|項目|種類|表示区分|入力チェック|概要|
|:--|:--|:--|:--|:--|
|MagazineManager|リンク|||雑誌一覧画面に遷移する。|
|ログアウト|リンク|||ログアウト処理を行う。<br>ログアウト後は雑誌一覧画面に遷移する。|
|雑誌新規登録|ラベル|||タイトル|
|雑誌名|ラベル||||
|雑誌名|テキストボックス||必須入力<br>文字列長|0～30文字入力可能。|
|号数|ラベル||||
|号数|テキストボックス||必須入力<br>文字列長|0～20文字入力可能。|
|登録|ボタン|||雑誌を登録する。|
|戻る|リンク|||雑誌一覧画面へ遷移する。|
|エラーメッセージ|ラベル|||登録処理前の入力チェックで、エラーメッセージがある場合表示する。|

## 動作

### 初期表示
#### 概要
雑誌新規登録画面を表示する。
- 区分：サーバ処理
- トリガー：GETリクエストを受信
- リクエストURL：`/register`
- 実行権限：管理者のみ

#### シナリオ
- 正常系
    - 雑誌新規登録画面を表示する。
- 異常系
    - ログインしていないまたはセッションが切れた場合、アクセス拒否する。

### ルートに遷移
#### 概要
システムのルート画面（雑誌一覧画面）に遷移する。
- 区分：画面遷移
- トリガー：**MagazineManagerリンク**が押されたとき
- リクエストURL：`/`
- 実行権限：全て

#### シナリオ
- 正常系
    - システムのルート画面に遷移する。
- 異常系
    - なし

### ログアウト処理
#### 概要
共通のログアウト処理を呼び出す。
- 区分：サーバ処理
- トリガー：**ログアウトリンク**が押されたとき
- リクエストURL：`/logout`
- 実行権限：管理者のみ

#### シナリオ
- 正常系
    - ログアウト処理を行う。
- 異常系
    - なし

### 登録処理
#### 概要
雑誌を登録する。
- 区分：サーバ処理
- トリガー：**登録ボタン**が押されたとき
- リクエストURL：`/register/create`
- 実行権限：管理者のみ

#### シナリオ
- 正常系
    - フォームに入力された内容をもとに雑誌情報を登録する。
- 異常系
    - ログインしていないまたはセッションが切れた場合、アクセス拒否する。
    - 既にシステム上に同じ雑誌名と号数が登録されている場合、エラーメッセージを設定してエラー画面に遷移する。

### 戻る
#### 概要
雑誌一覧画面へ遷移する。
- 区分：画面遷移
- トリガー：**戻るリンク**が押されたとき
- リクエストURL：`/list`
- 実行権限：全て

#### シナリオ
- 正常系
    - 雑誌一覧画面へ遷移する。
- 異常系
    - なし

## エラーメッセージ

### 雑誌名
#### 未入力の場合
雑誌名が入力されていません。

#### 30文字以上入力された場合
雑誌名は30文字以内で入力してください。

### 号数
#### 未入力の場合
号数が入力されていません。

#### 20文字以上入力された場合
号数は20文字以内で入力してください。

