Troubleshooting
---

`zsh-syntax-highlighting.zsh` wraps ZLE widgets and analyzes the input line
buffer to decide on how certain parts should be highlighted. This leads to
some things that have to be considered and some issues.


### `zsh-syntax-highlighting.zsh` must be sourced at the end of the `.zshrc`

For `zsh-syntax-highlighting.zsh` to know about all custom widgets that have
been created (i.e., after all `zle -N` calls and after running `compinit`)
it is necessary that `zsh-syntax-highlighting.zsh` is sourced at the end
of `.zshrc`.  Widgets created later will work, but will not update the
syntax highlighting.


### Some special widgets are not wrapped by `zsh-syntax-highlighting.zsh`

`zsh-syntax-highlighting.zsh` does not wrap or bind all the special `zle-*`
widgets provided by zsh. Since the `zle-*` namespace is special, custom 
widgets should not be named that way.


### Highlighting in an isearch minibuffer does not work

In `zsh` versions before v5.3 it is not possible to know if an isearch
minibuffer is active and parts of the text should be underlined (or
otherwise highlighted). Therefore it is not possible to apply highlighting
by `zsh-syntax-highlighting.zsh` while still highlighting the matched part
of the search.
