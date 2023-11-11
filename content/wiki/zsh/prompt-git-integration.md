+++
title = 'Prompt Git integration'
summary = 'Show Git information in the zsh prompt'
date = 2023-11-11T12:54:26+01:00
draft = false
+++

```zsh
autoload -Uz add-zsh-hook vcs_info
setopt prompt_subst
add-zsh-hook precmd vcs_info

zstyle ':vcs_info:*' enable git svn
zstyle ':vcs_info:*' check-for-changes true
zstyle ':vcs_info:*' unstagedstr ' *'
zstyle ':vcs_info:*' stagedstr ' +'
zstyle ':vcs_info:git:*' formats '(%b%u%c)'
zstyle ':vcs_info:git:*' actionformats '(%b|%a%u%c)'

PROMPT='%1~ %F{red}${vcs_info_msg_0_}%f %# '
```
