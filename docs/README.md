# MagagineManager 開発ドキュメント

> これはMagazineManagerの開発用ドキュメントです。  
> [tenohira-xyz/MagazineManager: 雑誌管理用webシステム](https://github.com/tenohira-xyz/MagazineManager)  

## システムの概要
[システムの概要](overview.md)

## 改善
[改善リスト](improvement.md)

## 基本設計

### 画面一覧
- [画面一覧](screen-list.md)
    - [ログイン画面](screen-login.md)
    - [雑誌一覧画面](screen-magazinelist.md)
    - [雑誌新規登録画面](screen-register.md)
    - [雑誌詳細画面](screen-detail.md)
    - [目次画面](screen-contents.md)
    - [索引画面](screen-index.md)

### 画面レイアウト
- [ワイヤーフレーム](ui-wireframe.md)

## 詳細設計

### Controller層
- [ログイン画面コントローラクラス](controller-login.md)
- [雑誌一覧画面コントローラクラス](controller-magazinelist.md)
- [雑誌新規登録画面コントローラクラス](controller-register.md)
- [雑誌詳細画面コントローラクラス](controller-detail.md)
- [目次画面コントローラクラス](controller-contents.md)
- [索引画面コントローラクラス](controller-index.md)

### Service層
- [雑誌サービスクラス](service-magazine.md)
- [記事サービスクラス](service-article.md)
- [キーワードサービスクラス](service-keyword.md)

### Repository層
- [雑誌リポジトリクラス](repository-magazine.md)
- [記事リポジトリクラス](repository-article.md)
- [キーワードリポジトリクラス](repository-keyword.md)

### Form
- [雑誌一覧画面のフォーム](form-magazinelist.md)
    - [フォームの雑誌クラス](form-magazinelist.md#フォームの雑誌クラス)
- [雑誌新規登録画面のフォーム](form-register.md)
- [雑誌詳細画面のフォーム](form-detail.md)
- [目次画面のフォーム](form-contents.md)
    - [フォームの記事クラス](form-contents.md#フォームの記事クラス)
- [索引画面のフォーム](form-index.md)
    - [フォームのキーワードクラス](form-index.md#フォームのキーワードクラス)

### Model(Entity)
- [雑誌クラス](model-magazine.md)
- [記事クラス](model-article.md)
- [キーワードクラス](model-keyword.md)

### 例外
- [独自に定義する例外](exception.md)

### セキュリティ設定
- [セキュリティ設定クラス](security-settings.md)

### データベース仕様
- [データベース仕様](database.md)

## テスト
- [単体テストのテストケース一覧](ut-list.md)
- [結合テストのテストケース一覧](lt-list.md)

