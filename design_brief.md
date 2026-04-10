# Blue Bee Ink — Design Brief
## Claude Codeへの引き継ぎドキュメント

---

## クライアント情報

| 項目 | 内容 |
|------|------|
| サイト名 | Blue Bee Ink |
| クライアント | 吉川カンナ（Kanna Yoshikawa）|
| 職種 | グラフィックレコーダー |
| 拠点 | 神戸（Kobe, Japan）|
| 強み | ヘルスケア × バイリンガル（日英）× 多様性 × アニメーション |
| 背景 | 外資系製薬企業出身 |
| 目的 | 受注獲得（グラレコサービス）|
| ターゲット | 会議主催者・ファシリテーター・テレビ関係者・ヘルスケア企業 |

---

## デザイン方向性

### コンセプト
**Gallery White × Vivid Blue** — 余白を生かした清潔感のある白ベースに、3段階の青でメリハリをつける。Drawing Impact（drawingimpact.com）の「中央コンテンツ・迷いのない構成」を参考に。

### カラーパレット（確定）

```css
/* 3段階の青 */
--sky-tint:   #e4f3f9;  /* 背景・フォーム面・セクション塗り */
--sky-blue:   #7cb8d4;  /* 枠線・引用線・サークル枠・ロゴの蜂 */
--vivid-blue: #1A8FD1;  /* CTAボタン・ナビ下線・カレンダー空き日・見出しイタリック */

/* ベース */
--navy:  #1a3040;  /* フッター背景・見出しテキスト */
--white: #ffffff;  /* ページ背景 */
--text-main: #1a3040;
--text-sub:  #5a7a88;
```

### タイポグラフィ
- 見出し：**Georgia**（セリフ体）— 上品さと洗練感
- 本文・UI：**サンセリフ**（システムフォント or Googleフォント）
- 見出しのイタリック部分に `--vivid-blue` を使ってアクセント

### レイアウト原則
- **中央寄せ1カラム**、max-width: 660px で全セクション統一
- Drawing Impact型の「迷いのない構成」
- モバイルファースト：グリッドは自動縮小（3列→2列など）
- ナビは固定（sticky）、ボーダー下線は `--vivid-blue`

---

## サイト構成（1ページ完結）

### ナビゲーション（固定）
```
Blue Bee Ink ロゴ（蜂マーク付き）｜ Home About Service Works Contact →（CTAボタン）
```

### 01 Hero
- キッカー：`GRAPHIC RECORDER · BILINGUAL · KOBE`（`--vivid-blue`）
- 見出し：`Ideas drawn into clarity.`（"clarity"部分をイタリック＋vivid blue）
- 本文（日本語）：複雑なアイデアを、伝わるビジュアルへ。ヘルスケア・多様性・バイリンガル対応。
- CTAボタン2つ：「お問い合わせ →」「Works を見る」
- ヒーロー画像エリア（後で実際の作品に差し替え）

### 02 About me
- 写真（丸形、`--sky-blue`ボーダー）
- 名前：吉川カンナ / タイトル：GRAPHIC RECORDER · BLUE BEE INK · KOBE
- 本文：外資系製薬企業での経験を活かし、神戸を拠点に…
- 推薦コメント（引用ブロック、左線`--sky-blue`、背景`--sky-tint`）
- 認定グラレコアンバサダーバッジ

### 03 Services（4つの円）
- 背景：`--sky-tint`
- 円4つ（白背景、枠線カラー違い）：
  - Medical（`--vivid-blue`枠）
  - Diversity（`--sky-blue`枠）
  - English（`--vivid-blue`枠）
  - Animation（`--sky-blue`枠）

### 04 Works
- フィルターピル（All / Medical / Diversity / Animation / Bilingual）
  - アクティブ：`--vivid-blue`塗り、非選択：`--sky-blue`枠
- 3列グリッド（モバイルは2列）
- 動画サムネイルには再生ボタン
- 「すべての作品を見る →」ボタン

### 05 Contact
- **カレンダー（カスタムデザイン）**
  - Googleカレンダー公開URLからiCal読み込み（または静的表示）
  - ヘッダー背景：`--vivid-blue`（白テキスト）
  - 空き日：`--vivid-blue`塗り、予約済み：`--sky-tint`塗り
  - 説明：「青い日付が対応可能な日程です」
- **Googleフォーム埋め込み**（iframeで本物のGoogleフォームを埋め込む）
  - フォームURL：後で差し替え
  - 項目：お名前 / 会社名（任意）/ メール / 依頼種類 / 希望時期 / 依頼内容
- **Newsletterフォーム**（別のGoogleフォームiframe）
  - 「グラレコ Tips・新作・イベント情報を月1回」

### フッター
- 背景：`--navy`（#1a3040）
- ロゴ（Georgia、`#b0d4e2`）
- © 2025 吉川カンナ · Kobe, Japan
- Instagram / LinkedIn / プライバシーポリシー

---

## システム構成

| 機能 | ツール | 費用 |
|------|--------|------|
| カレンダー表示 | Googleカレンダー公開URL読み込み | 無料 |
| お問い合わせ | Googleフォーム埋め込み | 無料 |
| メルマガ登録 | Googleフォーム（別フォーム） | 無料 |
| 通知 | Gmail自動通知 | 無料 |
| 回答管理 | Googleスプレッドシート | 無料 |

---

## Googleフォーム項目（確定）

お問い合わせフォーム：
1. お名前（必須）
2. 会社名・団体名（任意）
3. メールアドレス（必須）
4. ご依頼の種類（選択：Medical / Diversity / English / Animation / その他）
5. ご希望の時期
6. ご依頼内容・ご質問（テキストエリア）

---

## Claude Codeでやること（優先順）

1. [ ] Google Fontsの導入（見出し用セリフ体の検討：Playfair Display, Cormorant Garamondなど）
2. [ ] Heroセクションのアニメーション（フェードイン＋スクロール連動）
3. [ ] Worksのフィルター機能（JavaScriptでカテゴリ絞り込み）
4. [ ] 実際の作品画像・動画の組み込み（`/assets/`フォルダ）
5. [ ] Googleカレンダー公開URL連携（iCal解析またはAPI）
6. [ ] Googleフォームの実際のiframe埋め込み
7. [ ] モバイル実機確認・調整
8. [ ] サービスワーカー・OGP・SEOメタタグ
9. [ ] 本番サーバー公開

---

## 参考サイト

- drawingimpact.com（レイアウト構成の参考）
- byjuliabakay.com（タイポグラフィ・ヒーローレイアウト）
- verity.ink（バイリンガル×ヘルスケアの見せ方）
- kristenvisualnotes.com（友人のサイト、温かみの参考）

---

## ファイル構成（推奨）

```
blue-bee-ink/
├── index.html          ← メインファイル（このファイルがスタート）
├── design_brief.md     ← このファイル
├── assets/
│   ├── images/         ← 作品画像
│   ├── videos/         ← 作品動画
│   └── logo/           ← 蜂のロゴSVG
└── README.md
```
