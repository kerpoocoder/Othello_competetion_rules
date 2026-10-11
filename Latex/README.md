# قوانین مسابقات جهانی اتللو: پروژه LaTeX

Persian (right-to-left) LaTeX source of the reviewed translation of the *World Othello Championships Rules* (September 2019). The text comes from [`../Review/corrected_text.md`](../Review/corrected_text.md).

## Build

You need TeX Live (or MiKTeX) with XeLaTeX and the `xepersian` package.

```sh
cd Latex
latexmk            # uses ./latexmkrc → XeLaTeX
# or, without latexmk:
xelatex main.tex && xelatex main.tex   # second run fills in the table of contents
```

The output is `main.pdf`.

## Fonts

| Use | Font | Notes |
| --- | --- | --- |
| Body text | B Nazanin, B Nazanin Bold | |
| Main title | B Titr | |
| Latin words (WOF, MBS, …) | TeX Gyre Termes | Ships with TeX Live. |

The font files are included in `fonts/` (`BNazanin.ttf`, `BNazaninBold.ttf`, `BTitrBold.ttf`), so the project builds without installing anything. That includes Overleaf, if you upload the whole `Latex` folder. If the `fonts/` folder is missing, `main.tex` falls back to the system-installed fonts `B Nazanin`, `B Nazanin Bold` and `B Titr`.

## Layout

| Path | Contents |
| --- | --- |
| `main.tex` | Preamble: fonts, headings, lists, footer «- n -», watermark, title page |
| `sections/00-note.tex` | Translator's note and signature (title page) |
| `sections/01-general.tex` | الف. قوانین کلی و شرایط بازی |
| `sections/02-format.tex` | ب. ساختار مسابقات |
| `sections/03-semifinals.tex` | ج. نیمه‌نهایی‌ها و فینال |
| `sections/04-games.tex` | د. روند برگزاری و امتیازدهی بازی‌ها |
| `sections/05-enforcement.tex` | هـ. اجرای قوانین |
| `sections/06-appendix-a.tex` | پیوست الف: سیستم ترکیبی برایتول |
| `sections/07-appendix-b.tex` | پیوست ب: برنامه زمانی روز سوم |
| `images/` | WOF and Iran Othello logos, plus the faint background watermark built from them |

## Conventions in the sources

| Convention | Why |
| --- | --- |
| Headings carry their numbers in the text (`\band{۱. برگزاری}`, `\zirband{۲.۱ کشورها}`) | Cross-references such as «بند ب.۲» keep matching. |
| `\bakhsh` starts a new page and a top-level part (الف، ب، …). `\band`, `\zirband` and `\onvan` are the lower heading levels. | |
| Latin-script text is wrapped in `\lr{…}` | B Nazanin has no Latin glyphs. |
| Multi-part numbers are wrapped in `\LRE{…}`, e.g. `\LRE{۲\kern0pt.\kern0pt۱}` and `\LRE{۹:۳۰}` | Otherwise XeTeX shows them reversed. The `\kern0pt` around the dot is needed because xepersian treats a dot between digits specially. |
| Half-spaces are the Unicode ZWNJ character (U+200C), typed directly in the text. | |
| Lettered clauses use the `bandha` list with explicit labels: `\item[الف)]` | |
