
quaint-mathjax
==============

Embed math in Quaint using MathJax.

## Install

```bash
$ npm install quaint-mathjax
$ quaint -p mathjax file.q
```


## Usage

The plugin defines three operators:

* `$+[...]` inserts math inline
* `$$ ...` displays one or more equations
* `$@ref` inserts a reference to an equation

```
Inline math! $+[x_1 + x_2]

Display math:

$$ \sum_{i=1}^{1000} x_i + y_i^2 + z_i^3
```

### Environments and numbering

The `$$` operator can take an indented body. In that body, a few
forms are specially supported:

* `* equation` will add a non-numbered equation
* `# equation` will add a numbered equation
* `label # equation` will label an equation
  * Labelled equations can be referred to elsewhere using `$@label`

Equations prefixed with `*` or `#` will be on their own line, so there
is no need to append `\\` at the end:

```
$$
  * x & = y + z
  * x - y & = z
```

is equivalent to:

```
raw $$
  \begin{align}
    x & = y + z \\
    x - y & = z
  \end{align}
```

To the left of `$$` you can add any of the supported environments,
[listed here](http://mathjax.readthedocs.org/en/latest/tex.html#environments),
or `raw` which means not to insert begin/end directives at all.

The default environment is `align`.

NOTE: you shouldn't need the starred environments like `align*`,
because you can prefix each equation with `#` or `*` depending on
whether you want it to have a number or not.


### Wrap with a class

Instead of an environment, or in addition to it, you may specify class
descriptions and an id for an equations block:

```
.my-class#some-id $$
  * x & = y + z
  * x - y & = z
```

The above will wrap the equation with `<div class="my-class" id="some-id">...</div>`,
which means you can easily customize the display of various equations.


