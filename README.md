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

Dependency: inkscape, pdf2svg, pdfcrop, pdflatex, xclip
Usage: Typeset latex content into svg/png
