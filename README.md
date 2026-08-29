# 血圧管理アプリ 紹介ページ

Android アプリ「血圧管理」の紹介ページを置くリポジトリ。
GitHub Pages で公開するためだけのもので、アプリのソースは入っていない。

| ファイル | 内容 |
|---|---|
| `index.html` | ページ本体。1ファイルで完結している |
| `privacy.html` | プライバシーポリシー |

`privacy.html` だけページを分けてある。Play Console がポリシーの
URL での登録を必須にしているため。

```
https://miyama-job17.github.io/BloodPressureManagementAndroid/privacy.html
```

このファイルは生成物ではないので、直すときはここを直接編集する。
アプリの機能を変えて情報の扱いが変わったとき（広告の追加など）は、
本文と「最終改定」の日付・版数を必ず更新すること。

ページは上のタブで2つに分かれている。

| タブ | 中身 | URL |
|---|---|---|
| 紹介 | アプリの説明・画面・仕様 | `.../` |
| 使い方 | 操作マニュアル（全8章） | `.../#manual` |

章ごとにも直接開ける（`#manual-1` 〜 `#manual-8`）。
ページを分けずタブで切り替えているのは、`index.html` 1ファイルで
完結させたままにするため。

## 公開のしかた

GitHub の［Settings］→［Pages］で次を設定する。

| 項目 | 値 |
|---|---|
| Source | Deploy from a branch |
| Branch | `main` / `(root)` |

数分後に次の URL で見られるようになる。

```
https://miyama-job17.github.io/BloodPressureManagementAndroid/
```

## 直すには

**このリポジトリの `index.html` を直接編集しない。**

このファイルはアプリ本体のリポジトリで生成している。
文面やスタイルを直すときは、そちらの `tools/site/template.html` を編集して
再生成し、できた `html/index.html` をここへコピーする。

```
BloodPressureManagementCs（アプリ本体・非公開）
  tools/site/template.html      ← 紹介タブの文面・全体のスタイル
  tools/manual/content.py       ← 使い方タブの文面（操作マニュアルの原稿）
  tools/site/icon-128.png       ← 上のバーのロゴと favicon
  tools/site/build_site.py      ← python build_site.py で生成
  html/index.html               ← できたものを、このリポジトリへコピー
```

「使い方」タブは操作マニュアル（PDF）と同じ `content.py` から作っている。
文面を直したら、PDF（`tools/manual/build_manual.py`）と
このページの両方を作り直すこと。

画面写真は WebP、アイコンは PNG にして data URI で埋め込んであるため、
`index.html` 1ファイルだけで表示できる。
外部から読み込むのは Google Fonts の書体だけ。

## 公開したら直すところ

Google Play でアプリを公開したら、生成元のテンプレートで次の2か所を
実際の内容に合わせて、再生成し直す。

1. ヒーロー下の「現在テスト配布中。Google Play での公開を準備しています。」
2. ［画面を見る］ボタンを Play ストアへのリンクに差し替える

## 掲載内容について

ページに写っている血圧・脈拍・体重の数値は、動作確認のために
エミュレータへ入れた作りデータであり、実測値ではない。

区分の説明と免責事項は、アプリの基本設計書 7.5 の文言に合わせてある。
「診断」と読める表現を足さないこと。
