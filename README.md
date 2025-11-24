# Structure of the World – LaTeX Project

Dies ist das LaTeX-Projekt für das Buch **„Die Struktur der Welt- Mathematik zwischen Abstraktion un Realität“** in deutscher und englischer Version.

## 📂 Projektstruktur

```
photon-book/
├── bib/              # Zentrale Bibliothek (gemeinsam für de/en)
│   └── literatur.bib
│
├── de/               # Deutsche Version
│   ├── main.tex
│   ├── preamble.tex
│   ├── chapters/
│   ├── appendix/
│   ├── bilder/
│   └── cover/
│
├── en/               # Englische Version
│   ├── main.tex
│   ├── preamble.tex
│   ├── chapters/
│   ├── appendix/
│   ├── figures/
│   └── cover/
│
├── styles/           # Zentrale Styles und Makros
│   ├── boxes.sty     # Box-Definitionen (physikbox, mathebox, …)
│   ├── macros.sty    # eigene Befehle
│   ├── index.sty     # Index-Einstellungen (imakeidx/xindy)
│   └── photonbook.cls# (optional) Dokumentklasse
│
└── README.md
```

## 📖 Kompilieren

### 1. Deutsche Version
```bash
cd de
pdflatex main.tex
biber main
makeindex main.idx    # oder xindy, wenn in TeXstudio eingestellt
pdflatex main.tex
pdflatex main.tex
```

### 2. Englische Version
```bash
cd en
pdflatex main.tex
biber main
makeindex main.idx    # oder xindy
pdflatex main.tex
pdflatex main.tex
```

👉 In **TeXstudio** reicht es, `main.tex` zu kompilieren, wenn folgende Einstellungen aktiv sind:
- Bibliographie-Tool: **Biber**
- Index-Tool: **MakeIndex** oder **Xindy** (empfohlen für Umlaute)
- "Erzeugen & Ansicht" → Standard: `pdflatex → biber → makeindex → pdflatex ×2`

## 📚 Literatur

- Zentrale Bibliothek: `bib/literatur.bib`
- Wird in beiden Versionen mit  
  ```latex
  \addbibresource{../bib/literatur.bib}
  ```  
  eingebunden.

## 🔤 Index

- Definiert in `styles/index.sty` mit `imakeidx`
- Ausgabe am Ende von `main.tex`:
  ```latex
  \printindex[myindex]
  ```
- Ignoriere temporäre Index-Dateien in `.gitignore`:
  ```
  *.idx
  *.ind
  *.ilg
  ```

## 🗂️ GitHub-Hinweise

- Temporäre LaTeX-Dateien (aux, log, bbl, blg, toc, pdf …) sind in `.gitignore`.
- Im Repo liegen nur die **Quellen** (Tex, Bib, Bilder, Styles).
- PDFs werden lokal erzeugt, nicht im Repo gespeichert.

---

✍️ **Autor:** Christian Weilharter, Dipl.-Ing. (FH)  
📅 Stand: Oktober 2025
