+++
title = 'Basic completion'
summary = 'Basic zsh completion with vim-like navigation'
date = 2023-11-11T13:00:31+01:00
draft = false
+++

```zsh
zmodload zsh/complist
autoload -U compinit
compinit
_comp_options+=(globdots) #show hidden files
zstyle ':completion:*' menu select
zstyle ':completion:*' cache-path $XDG_CACHE_HOME/zsh/zcompcache #optional

# use vim keys in completion menu
bindkey -M menuselect 'h' vi-backward-char
bindkey -M menuselect 'k' vi-up-line-or-history
bindkey -M menuselect 'l' vi-forward-char
bindkey -M menuselect 'j' vi-down-line-or-history
```
