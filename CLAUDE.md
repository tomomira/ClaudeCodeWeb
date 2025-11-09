# Claude Code プロジェクト設定

このファイルは、Claude Codeがプロジェクトのコンテキストを理解するための設定ファイルです。
プロジェクト固有の規約、コマンド、スタイルガイドを記述します。

## プロジェクト概要

ClaudeCodeWeb - Claude Code向けのWebプロジェクト

## テクノロジースタック

<!-- プロジェクトで使用する技術を記述 -->
- **言語**: [例: TypeScript, JavaScript, Python]
- **フレームワーク**: [例: React, Next.js, Express]
- **パッケージマネージャー**: [例: npm, yarn, pnpm]
- **テストフレームワーク**: [例: Jest, Vitest, Pytest]
- **リンター**: [例: ESLint, Prettier]

## よく使うコマンド

<!-- プロジェクトでよく使うコマンドを記述 -->
```bash
# 開発サーバーの起動
# npm run dev

# ビルド
# npm run build

# テストの実行
# npm run test

# 型チェック
# npm run typecheck

# リント
# npm run lint

# フォーマット
# npm run format
```

## コードスタイルとコンベンション

### 一般的なルール

- **IMPORTANT**: すべてのコードは一貫性のあるスタイルに従う
- インデント: 2スペース（タブではなくスペースを使用）
- 文字列: シングルクォート `'` を優先（JSXではダブルクォート）
- セミコロン: プロジェクトの慣習に従う

### モジュールシステム

- ES Modules（`import`/`export`）を使用
- CommonJS（`require`）は使用しない
- 可能な限りimportを分割代入する
  ```javascript
  // Good
  import { foo, bar } from 'module'

  // Avoid
  import module from 'module'
  const foo = module.foo
  ```

### 命名規則

- **コンポーネント**: PascalCase（例: `UserProfile`, `NavigationBar`）
- **ファイル名（コンポーネント）**: PascalCase（例: `UserProfile.tsx`）
- **ファイル名（ユーティリティ）**: kebab-case（例: `format-date.ts`）
- **関数・変数**: camelCase（例: `getUserData`, `isActive`）
- **定数**: UPPER_SNAKE_CASE（例: `API_ENDPOINT`, `MAX_RETRIES`）
- **型・インターフェース**: PascalCase（例: `User`, `ApiResponse`）

### ファイル構成

<!-- プロジェクト構造を記述 -->
```
src/
  ├── components/     # 再利用可能なコンポーネント
  ├── pages/          # ページコンポーネント
  ├── utils/          # ユーティリティ関数
  ├── hooks/          # カスタムフック
  ├── types/          # 型定義
  ├── styles/         # スタイルファイル
  └── tests/          # テストファイル
```

## ワークフロー

### 開発フロー

1. **コード変更前**: 既存のコンポーネント・ユーティリティを確認
2. **コード変更後**: 型チェックとリントを実行
3. **テスト**: 関連するテストを実行（全体ではなく必要な部分のみ）
4. **コミット前**: ビルドが成功することを確認

### テスト戦略

- **IMPORTANT**: 新しい機能には対応するテストを作成
- ユニットテストを優先
- 可能な限り単一のテストを実行してパフォーマンスを向上
- テストが失敗した場合は、コードを修正してから次に進む

### 型安全性

- **YOU MUST**: TypeScriptを使用する場合、すべての関数に適切な型を付ける
- `any`型の使用は避ける（やむを得ない場合は`unknown`を検討）
- 型定義ファイル（`types/`）に共通の型を集約

## Git とリポジトリエチケット

### ブランチ戦略

- メインブランチ: `main` または `master`
- フィーチャーブランチ: `feature/機能名`
- バグフィックス: `fix/バグ名`
- Claude Code専用: `claude/説明-セッションID`

### コミットメッセージ

Conventional Commitsフォーマットに従う:

```
type(scope): subject

body (optional)
```

**Type:**
- `feat`: 新機能
- `fix`: バグフィックス
- `docs`: ドキュメントのみの変更
- `style`: コードの意味に影響しない変更（空白、フォーマット等）
- `refactor`: リファクタリング
- `test`: テストの追加・修正
- `chore`: ビルドプロセスやツールの変更

**例:**
```
feat(auth): ユーザー認証機能を追加

- JWT認証を実装
- ログイン/ログアウトAPIを作成
```

### コミット粒度

- **IMPORTANT**: 一つのタスクに対して一つのコミット
- 大きな変更は複数の小さなコミットに分割
- 無関係な変更を一つのコミットにまとめない

## セキュリティ

- **CRITICAL**: APIキー、パスワード、トークンなどの機密情報をコードに含めない
- 環境変数（`.env`ファイル）を使用し、`.gitignore`に追加
- ユーザー入力は常にバリデーション・サニタイズを行う
- OWASP Top 10の脆弱性に注意（SQL injection, XSS, CSRF等）

## パフォーマンス

- バンドルサイズを最適化（不要な依存関係を避ける）
- 可能な限り遅延ロード（lazy loading）を使用
- 画像やアセットを最適化

## アクセシビリティ

- セマンティックHTMLを使用
- 適切なARIA属性を追加
- キーボードナビゲーションをサポート
- WCAG 2.1 AA基準を目指す

## その他の重要なルール

- **言語**: コメントとドキュメントは日本語で記述（コードは英語）
- **エラーハンドリング**: すべての非同期処理に適切なエラーハンドリングを実装
- **ログ**: 開発用のconsole.logは本番環境に残さない
- **依存関係**: 新しいパッケージを追加する前に、既存の依存関係で実現できないか確認

## カスタマイズ方法

このファイルはプロジェクトの成長とともに更新してください：

1. Claude Codeとの対話中に `#` キーを押すと、Claudeが自動的に指示をCLAUDE.mdに追加
2. チームメンバーと共有するため、CLAUDE.mdはgitにコミット
3. 個人的な設定は `CLAUDE.local.md` に記述し、`.gitignore`に追加

## 参考リソース

- [Claude Code公式ドキュメント](https://docs.claude.com/claude-code)
- [Claude Code ベストプラクティス](https://www.anthropic.com/engineering/claude-code-best-practices)

---

**Note**: このファイルはプロジェクトの要件に応じてカスタマイズしてください。
不要なセクションは削除し、必要なセクションは詳細を追加してください。
