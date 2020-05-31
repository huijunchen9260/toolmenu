# Toolmenu

A simple toolbox using dmenu with corresponding scripts

## Usage:

Put any script in the same directory with `toolmenu`, and use `toolmenu` to call them in `dmenu` prompt.

## Scripts

### archwiki

Dependency: `arch-wiki-doc`(use `sudo pacman -S arch-wiki-doc` to install), `dmenu`

Usage: open offline arch wiki html in your browser.

### calc

Dependency: `dmenu`, `Rscript`, `xclip`

Usage: do simple calculation on dmenu.

### inputmenu

Dependency: `dmenu`, `xinput`

Usage: Modify xinput devices in dmenu

### lidsuspend

Dependency: `dmenu`, `systemd`

Usage: Turn on/off lid-suspend

### manman

Dependency: `man`, `dmenu`

Usage: Search man page

### manpdf

Dependency: `man`, `dmenu`, `zathura`

Usage: Search man page and export to pdf

### manposix

Dependency: `man`, `dmenu`

Usage: Search POSIX man page

### manrandom

Dependency: `man`, `find`, `shuf`

Usage: generate random man page

### search

Dependency: `dmenu`, `xdg-open`

Usage: search in websites

### teximage

Dependency: `inkscape`, `pdf2svg`, `pdfcrop`, `pdflatex`, `xclip`, `dmenu`/`fzf`

Usage: Typeset latex content into svg/png

```
Arguments:
-a: Action: 'new content' or 'clear'
-p: use menu system other than dmenu
-o: output as 'tex'/'svg'/'png' to clipboard
-h: print help
```

### inkfig

Dependency: `inkscape`, `dmenu`

Usage: Automate latex and inkscape workflow. [This link](https://streamable.com/lrdmsu) demonstrate the usage.

```
Arguments:
-d: Specify project directory
-n: Specify imgname
-p: use menu system other than dmenu
-h: print help
```

Without `-n` argument, `inkfig` allows user to edit existing svg files.

Required latex preamble:

```tex
\usepackage{import}
\usepackage{pdfpages}
\usepackage{transparent}
\usepackage{xcolor}

\newcommand{\inkfig}[2][1]{%
    \def\svgwidth{#1\columnwidth}
    \import{./figures/}{#2.pdf_tex}
}

\pdfsuppresswarningpagegroup=1
```

Recommend ultisnip code snippet:

```
snippet inkfig "Figure environment" b
\begin{figure}[${3:ht}]
	\centering
	\inkfig[$2]{${4:${1/\W+/-/g}}}
	\caption{${1:${VISUAL}}}
	\label{fig:${5:${1/\W+/-/g}}}
\end{figure}
endsnippet
```
Use `$2` to adjust the percentage of figure width relative to the page width.

Recommend `.vimrc` setup

```vimL
autocmd FileType tex inoremap <leader>i <ESC>vi{y:!inkfig -d %:p:h -n <C-R>+<CR>
autocmd FileType tex nnoremap <leader>i :!inkfig -d %:p:h<CR>
```

### inkmenu and inkstyle

`inkmenu` is the `dmenu` interface to control `inkstyle`.

`inkstyle` use command line options to apply inkscape styles. [This link](https://streamable.com/4vngts) demonstrate the usage.

```
Usage:
inkstyle [OPTIONS] [ARGS]

Help Options:
  -h					Show help options
Style Options:
  -a, 					Create end-side arrow
  -A, 					Create both start-side and end side arrow
  -f, 					Fill with 0 opacity
  -F, 					Fill with middle opacity
  -b, 					Fill with high opacity
  -B, 					Fill with perfect opacity
  -c, 					Change stroke color, require argument
  -C, 					Change fill color, require argument
  -d, 					Dash stroke style 1
  -D, 					Dash stroke style 2
  -x, 					Dash stroke style 3
  -X, 					Dash stroke style 4
  -w, 					Change stroke to normal width
  -W, 					Change stroke to middle width
  -t, 					Change stroke to thick width
  -T, 					Change stroke to very thick width
  -r, 					Restore to default style
```
