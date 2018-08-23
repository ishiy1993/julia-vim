# julia-vim

<p align="center"><img src="logo.png" alt="julia-vim logo"/></p>

[Julia] support for Vim.

**[INSTALLATION INSTRUCTIONS]**

[Julia]: http://julialang.org/
[Installation instructions]: INSTALL.md

## Complete documentation

The full documentation is available from Vim: after installation, you just need to type `:help julia-vim`.

The remainder of this README will only give an overview of some of the features:

* [Block-wise movements and block text-objects](#block-wise-movements-and-block-text-objects)
* [Changing syntax highlighting depending on the Julia version](#changing-syntax-highlighting-depending-on-the-julia-version)

## Block-wise movements and block text-objects

This plug-in defines mappings to move around julia blocks (e.g. `if/end`, `function/end` etc.) and to
manipulate them as a whole (analogously to the standard `w`, `b` etc. commands to move on words, and to
the `aw`, `iw` commands which allow to manipulate them). These require the `matchit` plugin, which is usually
distributed with ViM but must be explicitly enabled, e.g. adding this to your `.vimrc` file:

```vim
runtime macros/matchit.vim
```

The default mappings use `]]`, `][`, `[[`, `[]`, `]j`, `]J`, `[j`, and `[J` for the movements
and `aj`, `ij` for the selections. These can be disabled collectively by setting `g:julia_blocks` to `0`,
or they can be remapped and/or disabled individually by defining a `g:julia_blocks_mapping` variable.
See the documentation for details.

Note that this feature requires Vim version 7.4 or higher.

## Changing syntax highlighting depending on the Julia version

The pluign supports syntax highlighting different versions of Julia. By default, the highlighting scheme assumes
the latest stable release of Julia (currently, version 1.0; the plugin does not differentiate between 0.7 and 1.0),
but the previous one and the latest version under development are also supported. You can set a global default in
your `.vimrc`, e.g. if you follow Julia's master you can use:

```
let g:default_julia_version = "devel"
```

or if you are still using Julia 0.6 you can use:

```
let g:default_julia_version = "0.6"
```

You can also switch version for a particular buffer, by using the `julia#set_syntax_version()` function, e.g.
by typing in Vim:

```
:call julia#set_syntax_version("0.6")
```
