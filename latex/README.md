# Latex

## Formatting Error

> You may need to install the File::HomeDir module

```shell
cpan
install File::HomeDir
```

## VS Code Settings

```json
{
  "latex-workshop.latex.tools": [
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": ["-shell-escape", "-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOCFILE%"]
    },
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": ["-shell-escape", "-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOCFILE%"]
    },
    {
      "name": "bibtex",
      "command": "bibtex",
      "args": ["%DOCFILE%"]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": ["%DOCFILE%"]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "PdfLatex",
      "tools": ["pdflatex"]
    },
    {
      "name": "XeLatex",
      "tools": ["xelatex"]
    },
    {
      "name": "BibTex",
      "tools": ["bibtex"]
    },
    {
      "name": "pdf->biber->pdf*2",
      "tools": ["pdflatex", "biber", "pdflatex", "pdflatex"]
    },
    {
      "name": "xe->bibtex->xe*2",
      "tools": ["xelatex", "bibtex", "xelatex", "xelatex"]
    },
    {
      "name": "pdf->bibtex->pdf*2",
      "tools": ["pdflatex", "bibtex", "pdflatex", "pdflatex"]
    }
  ],
  "latex-workshop.latexindent.path": "/usr/local/texlive/2024/bin/universal-darwin/latexindent",
  "latex-workshop.message.error.show": true,
  "latex-workshop.message.warning.show": true,
  "latex-workshop.latex.autoClean.run": "onBuilt"
}
```

