# Troubleshooting Guide - LaTeX on GitHub Codespaces

## Common Issues and Solutions

### 1. Codespace Build Takes Too Long

**Problem:** The initial Codespace creation takes more than 10 minutes.

**Solution:** 
- This is normal for the first build as TeX Live Full (~6GB) is being installed
- Subsequent rebuilds will be faster due to layer caching
- Be patient during the first setup

**Alternative:**
If you want a faster build, you can modify `.devcontainer/Dockerfile` to use `texlive-base` instead of `texlive-full`, but this will have fewer packages available.

### 2. LaTeX Compilation Errors

**Problem:** You see errors like `! LaTeX Error: File 'xxx.sty' not found.`

**Solutions:**
- The package might not be installed (unlikely with texlive-full)
- Check the package name spelling
- Try rebuilding the container: `Ctrl+Shift+P` → "Rebuild Container"

**Common Error Messages:**

```
! Undefined control sequence.
```
- You're using a command that doesn't exist
- Check spelling and required packages

```
! Missing $ inserted.
```
- Math mode error - you need to wrap math in `$...$` or `\[...\]`

```
! File ended while scanning use of \@xxx.
```
- Missing closing brace `}` somewhere

### 3. PDF Not Generating

**Problem:** LaTeX compiles without errors but no PDF appears.

**Solutions:**
1. Check the output directory:
   - Default: same directory as `.tex` file
   - Or check `./out/` directory
2. Look at the LaTeX Workshop output panel:
   - `View` → `Output` → Select "LaTeX Workshop" from dropdown
3. Try manual compilation:
   ```bash
   pdflatex yourfile.tex
   ```

### 4. Japanese Text Not Displaying

**Problem:** Japanese characters show as boxes or errors.

**Solutions:**
1. Make sure you're using the correct document class:
   ```latex
   \documentclass[uplatex]{jsarticle}
   ```
2. Use the correct compiler:
   - Use `uplatex` instead of `pdflatex`
   - Then run `dvipdfmx` to convert DVI to PDF
3. Ensure UTF-8 encoding:
   ```latex
   \usepackage[utf8]{inputenc}
   ```

### 5. Auto-Build Not Working

**Problem:** Saving the file doesn't trigger compilation.

**Solutions:**
1. Check LaTeX Workshop settings:
   - Open Command Palette: `Ctrl+Shift+P`
   - Type: "Preferences: Open Settings (JSON)"
   - Verify: `"latex-workshop.latex.autoBuild.run": "onSave"`
2. Manual build:
   - `Ctrl+Alt+B` (Windows/Linux) or `Cmd+Alt+B` (Mac)
3. Check the Output panel for errors

### 6. PDF Viewer Issues

**Problem:** PDF viewer doesn't open or shows blank.

**Solutions:**
1. Try different viewer:
   - Settings → LaTeX Workshop → View: PDF Viewer
   - Options: "tab", "browser", "external"
2. Disable browser popup blocker
3. Refresh the PDF manually:
   - Right-click on PDF → Reload

### 7. Permission Denied Errors

**Problem:** Errors related to file permissions.

**Solutions:**
1. Check file ownership:
   ```bash
   ls -la yourfile.tex
   ```
2. Fix permissions:
   ```bash
   chmod 644 *.tex
   chmod 755 .
   ```

### 8. Container Won't Start

**Problem:** Codespace fails to build with Dockerfile errors.

**Solutions:**
1. Check Dockerfile syntax
2. Verify the base image is accessible
3. Try rebuilding:
   - `Ctrl+Shift+P` → "Codespaces: Rebuild Container"
4. Check Docker build logs in the terminal

### 9. Extensions Not Loading

**Problem:** LaTeX Workshop extension doesn't appear.

**Solutions:**
1. Check extensions panel: `Ctrl+Shift+X`
2. Manually install: Search "LaTeX Workshop" and install
3. Reload window: `Ctrl+Shift+P` → "Developer: Reload Window"
4. Rebuild container if needed

### 10. Slow Compilation

**Problem:** Compilation takes a very long time.

**Solutions:**
1. Large documents with many images:
   - Use draft mode: `\documentclass[draft]{article}`
   - Comment out `\usepackage{graphicx}` temporarily
2. Check for infinite loops in macros
3. Reduce the number of compilation passes

## Advanced Troubleshooting

### Viewing Build Logs

1. Open Output Panel:
   - `View` → `Output`
   - Select "LaTeX Workshop" from dropdown

2. View detailed logs:
   - Check terminal for manual compilation output
   - Look at `.log` files generated during compilation

### Resetting the Environment

If all else fails, try these in order:

1. **Reload Window:**
   ```
   Ctrl+Shift+P → Developer: Reload Window
   ```

2. **Rebuild Container:**
   ```
   Ctrl+Shift+P → Codespaces: Rebuild Container
   ```

3. **Full Rebuild:**
   ```
   Ctrl+Shift+P → Codespaces: Full Rebuild Container
   ```

4. **Create New Codespace:**
   - Delete current Codespace
   - Create a fresh one

### Getting Help

If you're still stuck:

1. Check the [LaTeX Workshop Wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki)
2. Search [TeX Stack Exchange](https://tex.stackexchange.com/)
3. Review LaTeX compilation logs (`.log` files)
4. Check GitHub Codespaces status page

## Tips for Avoiding Issues

1. **Always save your work** before closing Codespace
2. **Use version control** - commit your `.tex` files regularly
3. **Test with simple documents** before creating complex ones
4. **Keep packages minimal** - only use what you need
5. **Use meaningful file names** - avoid spaces and special characters

## Quick Reference

### Essential Commands

```bash
# English documents
pdflatex document.tex

# Japanese documents
uplatex document.tex
dvipdfmx document.dvi

# Clean build files
rm *.aux *.log *.out *.dvi

# View available LaTeX commands
texdoc <package-name>
```

### Keyboard Shortcuts

- Build: `Ctrl+Alt+B` (Windows/Linux), `Cmd+Alt+B` (Mac)
- View PDF: `Ctrl+Alt+V` (Windows/Linux), `Cmd+Alt+V` (Mac)
- Command Palette: `Ctrl+Shift+P` (Windows/Linux), `Cmd+Shift+P` (Mac)

---

**Still having issues?** Create an issue in this repository with:
- Error message (full text)
- Your `.tex` file content
- LaTeX Workshop output
- Steps to reproduce

Happy LaTeXing! 📝
