# UMBS Arduino/Programming Reference

# Repo Structure

The project's actual reference materials are written in Sphinx-compatible reST
(`.rst` files): these files, and their build file can be found in the `docs/`
folder.

Project organization, brainstorming, and planning materials can be found in the
`devref/` folder.

# Compilation

These materials are written in [Sphinx-compatible](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html#).
[reStructuredText](http://www.sphinx-doc.org/es/stable/rest.html). This makes it
possible to "build" these materials into different formats, especially HTML
(for display on a website) and PDF (to be printed in hardcopy or distributed
digitally). As of the time of writing, only HTML output can be built.

Build prerequisites are, at the time of writing,

* A recent version of Python (3.6 or higher) and [pip](https://pip.pypa.io/en/stable/).
* [`sphinx`](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html#)
  itself (`pip install --user sphinx`)
* An existing LaTeX build environment, as could be installed (on Ubuntu) with
  `sudo apt install texlive-full texlive-latex-extra`. Additional prerequisites
  (also `apt`-installable packages, probably not exhaustive) are listed below:
  * `dvipng`, for rendering math equations as images.

The primary Makefile for this project is located in the `docs/` folder:
all of the Makefile targets mentioned below should be run from the `docs/`
folder, even when not otherwise stated.

To compile into HTML, to be viewed in a browser, run,

```bash
$ cd docs
$ make html
```

Output will be in the `docs/build` folder (e.g. `docs/build/html/index.html` for
the "homepage").

To delete all built artifacts, run,

```bash
$ make clean
```
