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
\let\header\big
\let\subheader\large

\newslide

\topfill{.333}
{\center %
    \header My presentation
    \subheader (with subtitle)}

\newslide

\topfill{.4}
{\center 
    Thank you for attending my talk.}

\bye
```

[See result](experiment.pdf)

## Using

`\input nobeamer.tex` in your TeX file. Use `pdftex` to compile the presentation into a pdf. `latexmk` can be made to use `pdftex` by creating a file named `latexmkrc` with the following contents:

```
$latex = 'pdftex %O %S'
```

You will have to place a copy of nobeamer.tex in your project directory. MiKTeX is recommended to automatically include the necessary font dependencies, as well as `eplain.tex`.

## Commands provided

* Font sizes, from largest to smallest:
    + `\big`
    + `\large`
    + `\regular`
    + `\small`
    + `\smaller`
    + `\tiny`
* `\newslide` --- Clears the page (`\vfill\break`).
* `\topfill{<ratio>}` --- Inserts `\topglue` of `0pt plus <ratio>fill`.
* `\foldbottom` --- Inserts `-1fill` vertical glue.

## Why

Because I read up on TeX and liked its economy in concepts (when compared to LaTeX).

[beamer]: https://ctan.org/pkg/beamer?lang=en
[eplain]: https://tug.org/eplain/doc/eplain.pdf
