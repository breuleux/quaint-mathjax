
quaint-mathjax
==============

Embed math in Quaint using MathJax.

## Install

```bash
$ npm install quaint-mathjax
$ quaint -p mathjax file.q
```


## Usage

The plugin defines two operators, `$=[...]` and `$$ ...` for inline
and display math respectively.

```
Inline math! $=[x_1 + x_2]

Display math:

$$ \sum_{i=1}^{1000} x_i + y_i^2 + z_i^3

You can also display equations using an `align` block, like this:

$$
  \begin{align}
    x & = y + z \\
    x - y & = z
  \end{align}

```


