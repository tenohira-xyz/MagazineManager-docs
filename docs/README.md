# MagagineManager 開発ドキュメント

> これはMagazineManagerの開発用ドキュメントです。  
> [tenohira-xyz/MagazineManager: 雑誌管理用webシステム](https://github.com/tenohira-xyz/MagazineManager)  

## 基本設計

### 画面一覧
- [画面一覧](screen-list.md)
    - [ログイン画面](screen-login.md)
    - [雑誌一覧画面](screen-magazinelist.md)
    - [雑誌新規登録画面](screen-register.md)
    - [雑誌詳細画面](screen-detail.md)
    - [目次画面](screen-contents.md)
    - [索引画面](screen-index.md)

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



