# LaTeX on GitHub Codespaces - Quick Start Guide

このガイドは、GitHub Codespaces上でLaTeX環境をすぐに使い始めるための手順を説明します。

## 🚀 セットアップ（初回のみ）

1. GitHubのこのリポジトリページで緑色の「Code」ボタンをクリック
2. 「Codespaces」タブを選択
3. 「Create codespace on main」をクリック
4. 環境の構築を待つ（初回は5-10分程度かかります）
   - TeX Liveの完全版がインストールされます
   - 日本語対応のLaTeX環境が自動的に構築されます

## ✏️ 文書の作成と編集

### サンプルファイルを開く

1. エクスプローラーから `sample.tex`（英語）または `sample_ja.tex`（日本語）を開く
2. ファイルを編集
3. 保存すると自動的にコンパイルされます

### 新しい文書の作成

1. 新しい `.tex` ファイルを作成
2. 以下のテンプレートを使用：

**英語文書の場合:**
```latex
\documentclass[a4paper,12pt]{article}
\usepackage[utf8]{inputenc}

\title{My Document}
\author{Your Name}
\date{\today}

\begin{document}
\maketitle

Your content here...

\end{document}
```

**日本語文書の場合:**
```latex
\documentclass[uplatex,a4paper,12pt]{jsarticle}
\usepackage[utf8]{inputenc}

\title{私の文書}
\author{あなたの名前}
\date{\today}

\begin{document}
\maketitle

ここに内容を書きます...

\end{document}
```

## 🔨 コンパイル方法

### 方法1: 自動コンパイル（推奨）
- ファイルを保存すると自動的にコンパイルされます
- PDFは同じディレクトリまたは `out/` フォルダに生成されます

### 方法2: 手動コンパイル
- `Ctrl+Alt+B`（Windows/Linux）または `Cmd+Alt+B`（Mac）を押す
- または、エディタ右上の「TeX」ボタンから「Build LaTeX project」を選択

### 方法3: ターミナルから
```bash
# 英語文書
pdflatex sample.tex

# 日本語文書
uplatex sample_ja.tex
dvipdfmx sample_ja.dvi
```

### 方法4: VS Codeタスク
- `Ctrl+Shift+B`（Windows/Linux）または `Cmd+Shift+B`（Mac）を押す
- 利用可能なタスクから選択

## 📄 PDFの表示

### VS Code内で表示
- `Ctrl+Alt+V`（Windows/Linux）または `Cmd+Alt+V`（Mac）を押す
- または、エディタ右上の「View LaTeX PDF」ボタンをクリック

### ファイルをダウンロード
1. エクスプローラーで生成された `.pdf` ファイルを右クリック
2. 「Download」を選択

## 📦 パッケージの使用

この環境には `texlive-full` がインストールされているため、ほとんどのLaTeXパッケージが利用可能です：

```latex
\usepackage{amsmath}      % 数式
\usepackage{graphicx}     % 画像
\usepackage{hyperref}     % ハイパーリンク
\usepackage{listings}     % コードリスト
\usepackage{tikz}         % 図形描画
```

## 🎨 日本語文書の作成

日本語文書には `jsarticle`、`jsbook`、`jreport` などのクラスを使用します：

```latex
\documentclass[uplatex,a4paper,12pt]{jsarticle}
\usepackage[utf8]{inputenc}

\title{日本語タイトル}
\author{著者名}
\date{\today}

\begin{document}
\maketitle

\section{はじめに}
日本語の文章を書くことができます。

\subsection{数式}
数式も問題なく使えます：
\begin{equation}
    E = mc^2
\end{equation}

\end{document}
```

## 🔧 トラブルシューティング

### コンパイルエラーが出る場合
1. エラーメッセージを確認（出力パネルに表示されます）
2. よくあるエラー：
   - `\end{document}` の記述漏れ
   - パッケージ名のスペルミス
   - 括弧やコマンドの閉じ忘れ

### PDFが表示されない場合
1. コンパイルが成功しているか確認
2. ブラウザのポップアップブロッカーを確認
3. ターミナルから手動でコンパイルを試す

### 日本語が表示されない場合
- `uplatex` を使用しているか確認
- `\documentclass[uplatex]{jsarticle}` のように `uplatex` オプションを指定

## 📚 参考リンク

- [LaTeX公式ドキュメント](https://www.latex-project.org/help/documentation/)
- [TeX Wiki（日本語）](https://texwiki.texjp.org/)
- [Overleaf Learn](https://www.overleaf.com/learn) - LaTeXチュートリアル

## 💡 ヒント

- 複雑な数式や図を含む場合は、コンパイルを2回実行
- 参考文献を使う場合は BibTeX の設定が必要
- 画像ファイルは `.png`、`.jpg`、`.pdf` が使用可能
- 大きなプロジェクトの場合は、ファイルを分割して `\input{}` や `\include{}` を使用

## 🎓 次のステップ

1. サンプルファイルを編集して試してみる
2. 自分の文書を作成する
3. より高度なLaTeXの機能を学ぶ
4. 必要に応じて環境をカスタマイズする

Happy LaTeXing! 📝✨
