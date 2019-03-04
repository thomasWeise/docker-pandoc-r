# [thomasWeise/docker-pandoc-r](http://hub.docker.com/r/thomasweise/docker-pandoc-r/): A Docker Container with [pandoc](http://pandoc.org/), [TeX Live](http://tug.org/texlive/), and [`R`](http://www.r-project.org/)

[![Docker Pulls](http://img.shields.io/docker/pulls/thomasweise/docker-pandoc-r.svg)](http://hub.docker.com/r/thomasweise/docker-pandoc-r/)
[![Docker Stars](http://img.shields.io/docker/stars/thomasweise/docker-pandoc-r.svg)](http://hub.docker.com/r/thomasweise/docker-pandoc-r/)

This is a [docker](https://www.docker.com) container intended for building electronic books from [pandoc's markdown flavor](http://pandoc.org/MANUAL.html#pandocs-markdown) by using [pandoc](http://pandoc.org/), [`R`](http://www.r-project.org/), and [TeX Live](http://tug.org/texlive/).

## 1. Building and Components

The image has the following components:

- [`TeX Live`](http://www.tug.org/texlive/)
- [`ghostscript`](http://ghostscript.com/)
- [`poppler-utils`](http://poppler.freedesktop.org/)
- [`cabal`](http://www.haskell.org/cabal/)
- [`pandoc`](http://pandoc.org/)
- [`imagemagick`](http://www.imagemagick.org/)
- several `pandoc` filters, namely
   + [`pandoc-citeproc`](http://github.com/jgm/pandoc-citeproc),
   + [`pandoc-crossref`](http://github.com/lierdakil/pandoc-crossref),
   + [`latex-formulae-pandoc`](http://github.com/liamoc/latex-formulae), and
   + [`pandoc-citeproc-preamble`](http://github.com/spwhitton/pandoc-citeproc-preamble)
- [`calibre`](http://calibre-ebook.com)
- [`R`](http://www.r-project.org/)

## 2. License

This image is licensed under the GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007, which you can find in file [LICENSE.md](http://github.com/thomasWeise/docker-pandoc-r/blob/master/LICENSE.md). The license applies to the way the image is built, while the software components inside the image are under the respective licenses chosen by their respective copyright holders.

## 3. Contact

If you have any questions or suggestions, please contact
[Prof. Dr. Thomas Weise](http://iao.hfuu.edu.cn/team/director) of the
[Institute of Applied Optimization](http://iao.hfuu.edu.cn/) at
[Hefei University](http://www.hfuu.edu.cn) in
Hefei, Anhui, China via
email to [tweise@hfuu.edu.cn](mailto:tweise@hfuu.edu.cn) and [tweise@ustc.edu.cn](mailto:tweise@ustc.edu.cn).
