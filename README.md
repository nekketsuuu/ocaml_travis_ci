<sup>Note: The newest README is on [`master`][master] branch.</sup>

## About

This repository shows the result of *Travis CI benchmarks for OCaml*.

Travis CI of a OCaml project sometimes takes a lot of time. In some projects, this is because Travis runs `make world` of the OCaml compiler for each single job. Therefore there are needs for a faster way for CI.

In this repository, the [`master`][master] branch contains a very simple "Hello, world!" project. Other branches have their own `.travis.yml` to use CI. The benchmark for each branch's method is written below. The details of results are [here](https://travis-ci.org/nekketsuuu/ocaml_travis_ci/branches).

## Benchmarks

| Branch                                                                   |   Time for `linux` (min) | Time for `osx` (min) | Memo                                                              |
|:-------------------------------------------------------------------------|-------------------------:|---------------------:|:------------------------------------------------------------------|
| [OPAM with cache][opam]                                                  |           8--10 (ubuntu) |                8--14 | uses `.travis-opam.sh` on [ocaml-ci-scripts].                     |
| [OPAM without cache][opam-without-cache]                                 |            7--9 (ubuntu) |                8--15 | uses `.travis-opam.sh` on [ocaml-ci-scripts].                     |
| [Docker (linux only)][docker]                                            |   3--4 (alpine & ubuntu) |      (not available) | uses `.travis-docker.sh` on [ocaml-ci-scripts].                   |
| [Docker for linux, OPAM for osx][docker-and-osx]                         |   3--4 (alpine & ubuntu) |               14--17 | uses `.travis-docker.sh` for linux and `.travis-opam.sh` for osx. |
| [Simplified Docker image][bobbypriambodo]                                | 1.5--4 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Simplified Docker image on `language: general`][bobbypriambodo-general] |   2--3 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Simplified Docker image on `language: bash`][bobbypriambodo-bash]       |   1--2 (alpine & ubuntu) |      (not available) | is based on [bobbypriambodo's method][bobbypriambodo-post].       |
| [Downloaded OPAM, without cache][zozozo]                                 |           6--14 (ubuntu) |      (not available) | is based on [zozozo's method][zozozo-post].                       |

### Notes

Each branch was executed only five times to measure the time. Because of this, **the error range may be large.**

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
