# nobeamer

(Extended) Plain TeX package to make no-nonsense presentations, if you *insist* on using TeX.

## Why nobeamer

[Beamer][beamer] is dreadful. It looks bad, introduces a lot of visual clutter into the presentation, and it's coercing a typesetting tool (LaTeX) into doing slides, which it wasn't made for. LaTeX itself greatly complicates TeX, though in exchange for useful features. PowerPoint doesn't have a good Linux equivalent.

(If you disagree with any of the above, you might find `nobeamer` silly. I respect your opinion. Otherwise, you might like `nobeamer`; or you might've written your own alternative already.)

`nobeamer` was written for when TeX suffices: write some content, set some sizes, add some spaces. [eplain][eplain] provides many of the comodities that we've come to expect from LaTeX, and the bare control over the glue in each slide helps correctly and pleasingly place the elements on the screen.

There's no magic: you just have to understand how boxes and glue work in TeX.

For example:

```tex
\input nobeamer.tex

\newslide

\topfill
\centering{
    \big My presentation

    \large (with subtitle)
}

\newslide

\topfill
\centering{ Thank you for coming to my talk. }

\bye
```

[See result](example.pdf)

## Using

`\input nobeamer.tex` in your TeX file. Use `pdftex` to compile the presentation into a pdf. `latexmk` can be made to use `pdftex` by creating a file named `latexmkrc` with the following contents:

```
$latex = 'pdftex %O %S'
```

You will have to place a copy of nobeamer.tex in your project directory. MiKTeX is recommended to automatically include the necessary font dependencies, as well as `eplain.tex`.

`nobeamer` sets the page size to 8×4 inches, with a horizontal margin of 0.4 inches, and a vertical margin of 0.2 inches.

## Commands provided

* Font sizes, from largest to smallest:
    + `\big`
    + `\large`
    + `\regular`
    + `\small`
    + `\smaller`
    + `\tiny`
* `\scriptsize` and `\scriptsciptsize`,
* `\newslide` clears the page (`\vfill\break`),
* `\topfill` inserts `\topglue` of `0pt plus 1fill`,
* `\fold` inserts `-1fill` vertical glue,
* `\centering{ ... }` centers text,
* `\mathcal`, `\mathrm`

## Why

Because I read up on TeX and liked its economy in concepts (when compared to LaTeX).

## Licence

`nobeamer` is licenced under a GNU General Public Licence v3 (GPL-3). This [informally means that][tldrlegal]

> You may copy, distribute and modify the software as long as you track changes/dates in source files. Any modifications to or software including (via compiler) GPL-licensed code must also be made available under the GPL along with build & install instructions.

See `LICENCE.txt` for the full text.

[beamer]: https://ctan.org/pkg/beamer?lang=en
[eplain]: https://tug.org/eplain/doc/eplain.pdf
[tldrlegal]: https://tldrlegal.com/license/gnu-general-public-license-v3-(gpl-3)
