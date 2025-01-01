# Development Rules

## 1. 開発手順

1. プロジェクト名の決定
2. GitHubリポジトリの作成
    - LICENSEはGPL-3.0
3. Rulesでmainブランチへの直接コミットを禁止
4. cloneして手元に持ってくる
5. 初期設定用のbranch、`initial-setup`を作成し、切り替える
6. プロジェクト構成が以下のようになるようにファイル、ディレクトリを作成する

```tree
.
├── docs/
│   └── .gitkeep
├── src/
│   └── .gitkeep
├── .env
├── .env.sample
├── .gitignore    # ファイル名を修正
├── LICENSE
└── README.md
```

## 2. ファイルのフォーマット

### `README.md`

```markdown
# {{ Project Name }}

{{ Project Description }}

{{ Demo Video or Image }}

## インストール方法

{{ Installation Method }}

## 使い方

{{ Usage }}

## 注意事項

{{ Note }}

## ライセンス

{{ License }}

## 開発者向け

{{ Information for Developer }}
```

### `.env`

1. `━`を使ってセクションで分ける
2. 各環境変数には必ず説明のコメントをつける
3. 文字列は必ずダブルクォーテーションで囲む
4. `env.sample`は`env`と同じ内容で作成する
5. `env.sample`でユーザーによる設定が必要な値には`TODO`をつける

#### Example

`.env`

```ini
# ━━━━━━━━━━━━━━━━━━━━
# Application Settings
# ━━━━━━━━━━━━━━━━━━━━
# アプリケーションで開くポート
APPLICATION_PORT=3000


# ━━━━━━━━━━━━━━━━━━━━
# YouTube API Settings
# ━━━━━━━━━━━━━━━━━━━━
# YouTube APIのAPIキー
YOUTUBE_API_KEY="your_api_key"
```

`.env.sample`

```ini
# ━━━━━━━━━━━━━━━━━━━━
# Application Settings
# ━━━━━━━━━━━━━━━━━━━━
# アプリケーションで開くポート
APPLICATION_PORT=3000

# ━━━━━━━━━━━━━━━━━━━━
# YouTube API Settings
# ━━━━━━━━━━━━━━━━━━━━
# YouTube APIのAPIキー
YOUTUBE_API_KEY="your_api_key" # TODO: <https://console.cloud.google.com/apis/credentials>から取得してきてここに設定してください
```

### source code

1. 基本的には1ファイルに1つのクラスとし、ファイル名とクラス名を一致させる
2. ファイルの先頭にコメントアウトでルートディレクトリからのパスを記載する
3. 言語に問わずスネークケースは使用せずにキャメルケースを使用する

#### Example

VideoManager.ts

```ts
// src/utils/VideoManager.ts

class VideoManager {
  constructor() {
    this.video = new Video();
  }
}
```
