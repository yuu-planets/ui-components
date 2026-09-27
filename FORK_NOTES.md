# UIコンポーネント集5選 フォーク一覧

**元ツイート**: [@bkdgiffug (lumxss) status 2101478951285879018](https://x.com/bkdgiffug/status/2101478951285879018)
**取得日**: 2026-09-26 / 2026-09-20 投稿
**フォーク先**: [yuu-planets](https://github.com/yuu-planets?tab=repositories&type=fork)
**総数**: 5/5 成功

## 元ツイート主張(要約)

> プログラマーが詰まるのはコードじゃなくてUIの美意識。
> **既製のキレイなコンポーネントをAIエージェントに投げて、選ばせ・調整させ・組み込ませる**のが横着ハック。
> Claude Code や Codex に **UI参考として渡す** ためのブックマーク必須5選。

---

## 5選 詳細比較

### 1. Beautiful UI

- **フォーク**: [yuu-planets/beautiful-ui](https://github.com/yuu-planets/beautiful-ui) ← [slev12397/beautiful-ui](https://github.com/slev12397/beautiful-ui)
- **★**: 276
- **公式サイト**: [beautifului.dev](https://www.beautifului.dev/)
- **作者**: Shane Levine / Turbo

**特性**:
- **AI-nativeインターフェース向け** のReactプリミティブ集
- `Ice Cream Harness` デモ同梱 — 実際にプリミティブでチャットUIを組んだサンプル
- スタック: Next.js (App Router) + Tailwind CSS v4 + TypeScript
- shadcn registry 形式 (`/r/registry.json` 提供)
- デザイントークンは `app/globals.css` の `@theme` 変数で定義
- ライト/ダーク両モード対応、cool blue tint 系統の neutral カラー
- ⚠️ `SidebarNav` は有料アイコンライブラリ `@central-icons-react` 依存 — `CENTRAL_LICENSE_KEY` 環境変数が必要、または自前アイコンに差し替え

**Claude Codeへの渡し方**:
```bash
# shadcn CLI 経由で追加
npx shadcn@latest add https://beautifului.dev/r/<component>.json
```

---

### 2. BeUI

- **フォーク**: [yuu-planets/ui-components](https://github.com/yuu-planets/ui-components) ← [starc007/ui-components](https://github.com/starc007/ui-components)
- **★**: 1,688
- **公式サイト**: [beui.dev](https://beui.dev/)
- **リポジトリ実名**: `ui-components` (公式は `@beui` namespace)

**特性**:
- **Motion (Framer Motion) ベース** のアニメーション付きReactコンポーネント **125個**
- スタック: React 19 + Tailwind CSS 4
- Bun パッケージマネージャ、TypeScript、a11y テスト組込
- shadcn registry からダウンロード可能

**Claude Codeへの渡し方**:
```bash
# 個別インストール
npx shadcn@latest add https://beui.dev/r/animated-toast-stack.json
```
- **Cursor / Claude Code / Codex 用の "skill" 配布あり** — エージェントから使える
- Pro版あり (ライセンスされた block workflow 機能)

---

### 3. Rare UI

- **フォーク**: [yuu-planets/rare-ui](https://github.com/yuu-planets/rare-ui) ← [swamimalode07/rare-ui](https://github.com/swamimalode07/rare-ui)
- **★**: 1,466
- **公式サイト**: [rareui.com](https://www.rareui.com/)

**特性**:
- 「**レア**」なanimated Reactコンポーネントに特化
- 各コンポーネントは **Motion** で実装、**`prefers-reduced-motion` を尊重**
- スタック: Next.js + Tailwind CSS + TypeScript
- shadcn registry 形式でインストール後は **コードは自分のもの** (パッケージ依存なし、restyle自由)
- **Jetpack Compose 版** (Android移植) も別リポで存在 — [dim971/rareui-android](https://github.com/dim971/rareui-android)
- **ライセンス**: MIT + Commons Clause + Attribution 必須
  - 個人/商用/クローズドソースで使用・改変・出荷OK

**Claude Codeへの渡し方**:
```bash
# shadcn CLI で追加
npx shadcn@latest add swamimalode07/rare-ui/{component-name}
```

---

### 4. Transitions

- **フォーク**: [yuu-planets/transitions.dev](https://github.com/yuu-planets/transitions.dev) ← [Jakubantalik/transitions.dev](https://github.com/Jakubantalik/transitions.dev)
- **★**: 4,360 (本記事5選で最多)
- **公式サイト**: [transitions.dev](https://transitions.dev/)
- **作者**: Jakub Antalik

**特性**:
- **CSSトランジション集** — コンポーネントではなくアニメの動き
- 無料: **18種類** (per-card "copy CSS" ボタン付き)、Pro: **36+** (React/TypeScript snippet 付き)
- 各トランジションに **duration / distance / easing のライブチューニング playground**
- npm パッケージ名は `transitions-refine`

**Claude Codeへの渡し方(独自のキラー機能)**:
```bash
# 個別追加
npx transitions-dev add card-resize

# 無料版全部
npx transitions-dev add --free
```

**Refine ツール** = **agent駆動のライブ companion**
  - 起動中のアプリに **timeline + Refine panel** を追加
  - 「Refine」クリックで、**選択した CSS/Motion トランジションを transitions.dev の motion tokens に整合させる** ようコーディングエージェントに依頼
  - → Claude Code/Codex と連携して、既存のバラバラなアニメを統一できる

---

### 5. shadcn/ui

- **フォーク**: [yuu-planets/ui](https://github.com/yuu-planets/ui) ← [shadcn-ui/ui](https://github.com/shadcn-ui/ui)
- **★**: 124,601 (別次元)
- **公式サイト**: [ui.shadcn.com](https://ui.shadcn.com/)
- **作者**: shadcn

**特性**:
- **UIコンポーネントライブラリの事実上の標準** (上記1〜4はすべてこのレジストリ形式に準拠)
- **npm パッケージにしない** = コンポーネントのソースコードを **自プロジェクトに直接コピー** する方式
  - 依存関係が発生しない、完全に自分でカスタマイズ可能
- ベース: **Radix UI** (a11y完備の低レベル primitive) + **Tailwind CSS**
- Composable, accessible, thoughtful defaults

**Claude Codeへの渡し方(すべてのshadcn系レジストリの基本コマンド)**:
```bash
# 個別インストール
npx shadcn@latest add button
npx shadcn@latest add dialog dropdown-menu form

# 初期化
npx shadcn@latest init
```

---

## 📊 5選 早見表

| # | 名前 | ★ | 特化領域 | インストール |
|---|------|---|---------|-----------|
| 1 | Beautiful UI | 276 | AI-nativeプリミティブ | `shadcn add ...beautifului.dev/r/*` |
| 2 | BeUI | 1,688 | Motion 125個 | `shadcn add ...beui.dev/r/*` |
| 3 | Rare UI | 1,466 | レアなアニメ、a11y配慮 | `shadcn add swamimalode07/rare-ui/*` |
| 4 | Transitions | 4,360 | CSSトランジション+Refineツール | `npx transitions-dev add *` |
| 5 | shadcn/ui | 124,601 | 全shadcnレジストリの元祖 | `shadcn add <name>` |

---

## 🎯 使い分けの目安

- **とにかく全部入り基盤** → `shadcn/ui` (Button, Dialog, Form など基本UI)
- **AI/チャットっぽいUI** → `Beautiful UI` (Ice Cream Harness みたいなの)
- **たくさんのアニメが欲しい** → `BeUI` (Motionベース125個)
- **人と違うアニメが欲しい** → `Rare UI` (「レア」を売りにしている)
- **既存アプリのアニメ品質を統一** → `Transitions` (Refine ツールで agent が調整)

## ⚠️ リプ欄で指摘されていた注意

- **制約を先に与えないと、AIエージェントは3つの違う角丸ボタンを1画面に混ぜてしまう**
- → 最初のプロンプトで「このライブラリからしか使うな、spacing と color も」と縛る

## 💡 使い方の型 (元ツイート流)

1. 対象サイトの `llms.txt` or レジストリ URL を Claude Code / Codex に渡す
2. 「このライブラリ **のみ** から拾って、以下の画面を組んで」と縛る
3. エージェントが自動で `shadcn add` を叩いて、自プロジェクトにソース配置
4. tweaks は自分でやるか、追加で指示

---

## リンク

- [フォーク一覧 (yuu-planets)](https://github.com/yuu-planets?tab=repositories&type=fork)
- [元ツイート](https://x.com/bkdgiffug/status/2101478951285879018)
