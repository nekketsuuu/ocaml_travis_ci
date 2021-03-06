<sup>Note: The newest README is on the [`master`][master] branch.</sup>

## About

This repository shows the result of my *Travis CI benchmarks for OCaml*.

A Travis CI job for a OCaml project sometimes takes a lot of time. In some projects, this is because Travis runs `make world` of the OCaml compiler for each single job. Therefore there are needs for a faster way of CI.

In this repository, the [`master`][master] branch contains a very simple "Hello, world!" project. Other branches have their own `.travis.yml` to use CI. The benchmark for each branch is written below. The details of the result are [here](https://travis-ci.org/nekketsuuu/ocaml_travis_ci/branches).

## Benchmarks

Note: Each branch was executed only five times to measure the time. Therefore, **the error range may be large.** Also, be aware that each branch runs different commands. For example, the Docker image `ocaml/opam` uses its local opam-repository, not the online one.

| Branch                                                                   |   Time for `linux` (min) | Time for `osx` (min) | Memo                                                              |
|:-------------------------------------------------------------------------|-------------------------:|---------------------:|:------------------------------------------------------------------|
| [OPAM 1 with cache][opam]                                                |           8--10 (ubuntu) |                8--14 | uses `.travis-opam.sh` on [ocaml-ci-scripts].                     |
| [OPAM 1 without cache][opam-without-cache]                               |            7--9 (ubuntu) |                8--15 | uses `.travis-opam.sh` on [ocaml-ci-scripts].                     |
| [Docker (linux only)][docker]                                            |   3--4 (alpine & ubuntu) |      (not available) | uses `.travis-docker.sh` on [ocaml-ci-scripts].                   |
| [Docker for linux, OPAM 1 for osx][docker-and-osx]                       |   3--4 (alpine & ubuntu) |               14--17 | uses `.travis-docker.sh` for linux and `.travis-opam.sh` for osx. |
| [Simplified Docker image][bobbypriambodo]                                | 1.5--4 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Simplified Docker image on `language: general`][bobbypriambodo-general] |   2--3 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Simplified Docker image on `language: bash`][bobbypriambodo-bash]       |   1--2 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Downloaded OPAM 2, without cache][zozozo]                               |           6--14 (ubuntu) |      (not available) | is based on [zozozo's method][zozozo-post].                       |

## See Also

* https://github.com/ocaml/ocaml-ci-scripts
* ["What are the best practices for setting up continuous integration for OCaml projects?"](https://discuss.ocaml.org/t/what-are-the-best-practices-for-setting-up-continuous-integration-for-ocaml-projects/1499) -- discuss.ocaml.org (posted on Jan 29, 2018)



   [ocaml-ci-scripts]: https://github.com/ocaml/ocaml-ci-scripts
   [master]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/master
   [opam]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/use-travis-opam-sh
   [opam-without-cache]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/use-travis-opam-sh-without-cache
   [docker]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/use-travis-docker-sh
   [docker-and-osx]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/use-travis-docker-sh-plus-osx
   [bobbypriambodo]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/bobbypriambodo
   [bobbypriambodo-general]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/bobbypriambodo-language-general
   [bobbypriambodo-bash]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/bobbypriambodo-language-bash
   [bobbypriambodo-post]: https://discuss.ocaml.org/t/what-are-the-best-practices-for-setting-up-continuous-integration-for-ocaml-projects/1499/3
   [zozozo]: https://github.com/nekketsuuu/ocaml_travis_ci/tree/zozozo
   [zozozo-post]: https://discuss.ocaml.org/t/what-are-the-best-practices-for-setting-up-continuous-integration-for-ocaml-projects/1499/6
