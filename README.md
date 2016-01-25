
quaint-mathjax
==============

Embed math in Quaint using MathJax.


## Install

    quaint --setup mathjax


## Usage

The plugin defines three operators:

* `$+[...]` inserts math inline
* `$$ ...` displays one or more equations
* `$@ref` inserts a reference to an equation

For example:

```
Inline math! $+[x_1 + x_2]

Display math!

$$ \sum_{i=1}^{1000} x_i + y_i^2 + z_i^3

References!

$$ emc2 # e = mc^2

For more information on the meaning of life, see $@emc2.

```

### Environments and numbering

The `$$` operator actually takes a second argument, which is the
environment for the equation(s) (default is `align`). This determines
how the body is formatted.

Regardless of the environment, a list of equations can be provided in
a body using the following syntax:

* `* equation` adds a *non-numbered* equation
* `# equation` adds a *numbered* equation
* `label # equation` *labels* an equation
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

To the left of `$$` you can add any of the environments
[listed here](http://mathjax.readthedocs.org/en/latest/tex.html#environments),
or `raw` which means not to insert begin/end directives at all.

The default environment is `align`.

**Note:** you shouldn't need the starred environments like `align*`,
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


## Options

There are no options at the moment.

