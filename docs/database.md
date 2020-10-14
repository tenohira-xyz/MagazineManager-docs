# データベース設定

## データベース製品
H2Database

## データベース名
### 開発用
`dev`
### テスト用
`test`
### 本番用
`userdata`

## テーブル設計
### 雑誌
#### 物理名
magazine

#### 定義
|論理名|物理名|型|桁数|備考|
|:--|:--|:--|:--|:--|
|雑誌ID|magazine_id|INT||主キー、自動採番(auto_increment)|
|雑誌名|name|VARCHAR|30|NOT NULL|
|号数|number|VARCHAR|20|NOT NULL|
|出版社|publisher|VARCHAR|20||
|発行日|issue_date|DATE|||
|更新日付|update_time|TIMESTAMP||NOT NULL|

### 記事
#### 物理名
article

#### 定義
|論理名|物理名|型|桁数|備考|
|:--|:--|:--|:--|:--|
|雑誌ID|magazine_id|INT||外部キー|
|セクション|section|VARCHAR|30||
|タイトル|title|VARCHAR|50||
|開始ページ|start_page|INT||NOT NULL|
|更新日付|update_time|TIMESTAMP||NOT NULL|

### キーワード
#### 物理名
keyword

#### 定義
|論理名|物理名|型|桁数|備考|
|:--|:--|:--|:--|:--|
|雑誌ID|magazine_id|INT||外部キー|
|単語|word|VARCHAR|50|NOT NULL|
|開始ページ|start_page|INT||NOT NULL|
|更新日付|update_time|TIMESTAMP||NOT NULL|


### ユーザマスタ
#### 物理名
m_user

#### 定義
|論理名|物理名|型|桁数|備考|
|:--|:--|:--|:--|:--|
|ユーザ名|name|VARCHAR|50|主キー|
|パスワード|password|VARCHAR|255||
|権限|authority|VARCHAR|20||

