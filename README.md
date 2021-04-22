# Dockerfiles for generating Docker images on M1 Mac of historical TeX Live archives

This repository contains Dockerfiles for generating Docker images of the following historical TeX Live archives.

* TeX Live 2017 (frozen)
* TeX Live 2018 (frozen)
* TeX Live 2019 (frozen)
* TeX Live 2020 (frozen)

## Original repositry

https://github.com/doraTeX/Docker-TLarchive

### More informations (in Japanese)

- https://qiita.com/doraTeX/items/51c219799a9292daa32d
- https://qiita.com/doraTeX/items/f40f9597763ca63daabb

## Features

### IPAex font embedding in TL2017 and TL2018 (for Japanese users)

In all of the above Docker images, the setting to embed IPAex fonts using `(u)pLaTeX` + `dvipdfmx`/`dvips` has already been applied.

## How to built images

You can use each of them like this.

```sh
docker build --no-cache=true -t texlive2020frozen .
```

## How to use the built images

You can use each of them like this.

```sh
$ alias tl2020="docker run --rm \
  --mount type=bind,src=\"\$(pwd)\",dst=/workdir \
  --mount type=volume,src=ltfontcache,dst=/usr/local/texlive/2020/texmf-var/luatex-cache/generic/fonts/otl \
  texlive2020frozen"
$ tl2020 pdflatex foobar.tex
```

In this example, `foobar.tex` in the current directory is compiled by pdfLaTeX included in the Docker container of TeX Live 2020.

# LICENSE

These Dockerfiles are distributed under [![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja).
