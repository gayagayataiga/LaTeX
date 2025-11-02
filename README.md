# LaTeX on GitHub Codespaces

This repository provides a fully configured LaTeX development environment for GitHub Codespaces.

## 🚀 Getting Started

### Using GitHub Codespaces

1. Click the green "Code" button on this repository
2. Select "Codespaces" tab
3. Click "Create codespace on main" (or your branch)
4. Wait for the environment to build (first time may take a few minutes)
5. Once ready, open any `.tex` file and start editing!

### Features

- **TeX Live Full**: Complete LaTeX distribution with all packages
- **Japanese Support**: Full support for Japanese documents with platex/uplatex
- **LaTeX Workshop**: VS Code extension for LaTeX editing with live preview
- **Auto-build**: Automatically compiles on save
- **PDF Viewer**: Built-in PDF viewer in VS Code

## 📝 Sample Documents

This repository includes sample documents to get you started:

- `sample.tex` - English LaTeX document sample
- `sample_ja.tex` - Japanese LaTeX document sample (日本語サンプル文書)

## 🔧 Usage

### Compiling LaTeX Documents

The LaTeX Workshop extension will automatically compile your documents when you save them. You can also:

1. Open a `.tex` file
2. Press `Ctrl+Alt+B` (or `Cmd+Alt+B` on Mac) to build
3. Press `Ctrl+Alt+V` (or `Cmd+Alt+V` on Mac) to view PDF

### Available Compilation Recipes

- **pdfLaTeX**: Standard PDF compilation
- **pdfLaTeX x2**: Compile twice (for references and citations)
- **platex → dvipdfmx**: For Japanese documents
- **uplatex → dvipdfmx**: For Unicode Japanese documents (recommended)

### Manual Compilation

You can also compile from the terminal:

```bash
# For English documents
pdflatex sample.tex

# For Japanese documents with platex
platex sample_ja.tex
dvipdfmx sample_ja.dvi

# For Japanese documents with uplatex (recommended)
uplatex sample_ja.tex
dvipdfmx sample_ja.dvi
```

## 📁 Project Structure

```
.
├── .devcontainer/          # Codespaces configuration
│   ├── devcontainer.json  # Codespaces settings and VS Code extensions
│   └── Dockerfile         # Container configuration with TeX Live
├── sample.tex             # English LaTeX sample
├── sample_ja.tex          # Japanese LaTeX sample
└── README.md             # This file
```

## 🛠️ Customization

### Adding LaTeX Packages

The environment includes `texlive-full`, which contains most LaTeX packages. If you need additional packages, you can:

1. Modify `.devcontainer/Dockerfile`
2. Add the package installation command
3. Rebuild the container

### VS Code Settings

LaTeX Workshop settings can be customized in `.devcontainer/devcontainer.json` under the `customizations.vscode.settings` section.

## 📚 Resources

- [LaTeX Documentation](https://www.latex-project.org/help/documentation/)
- [LaTeX Workshop Extension](https://github.com/James-Yu/LaTeX-Workshop)
- [Overleaf Learn](https://www.overleaf.com/learn) - Great LaTeX tutorials

## 日本語での説明

### 使い方

1. このリポジトリの緑色の「Code」ボタンをクリック
2. 「Codespaces」タブを選択
3. 「Create codespace on main」をクリック
4. 環境の構築を待つ（初回は数分かかります）
5. `.tex`ファイルを開いて編集開始！

### サンプル文書

- `sample_ja.tex` - 日本語のLaTeXサンプル文書

### コンパイル方法

ファイルを保存すると自動的にコンパイルされます。(現在まだエラーが発生する)
または：

```bash
# 日本語文書のコンパイル（推奨）
lualatex sample_1.txt
```

## License

MIT License - Feel free to use this template for your own projects!
