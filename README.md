# linux_conf
My Personal Linux configurations

# fontawesome
place fontawesome-webfont.ttf in ~/.fonts/

# i3 depends fontawesome
default i3   ~/.config/i3/config

# git status in bash

source ~/.git-prompt.sh
# bash git prompt
GIT_PS1_SHOWDIRTYSTATE=true
GIT_PS1_SHOWUNTRACKEDFILES=true
GIT_PS1_SHOWUPSTREAM="verbose"

git_current_branch_name="\$(__git_ps1 '%s' | sed 's/ .\+//' | sed -e 's/[\\\\/&]/\\\\\\\\&/g')"
git_status_substitutes=(
    "s/$git_current_branch_name//;" # remove branch temporarily
    "s/u//;" # upstream
    "s/+\([0-9]\+\)/▴\1/;" # outgoing
    "s/-\([0-9]\+\)/▾\1/;" # incoming
    "s/%/?/;" # untracked
    "s/+/✓/;" # staged
    "s/*/✕/;" # unstaged
    "s/\(.\+\)/($git_current_branch_name\1)/;" # insert branch again
)
git_status_command="\n└─ \$(__git_ps1 '%s'| sed \"${git_status_substitutes[@]}\")"

PS1="\n\[\033[0;32m\]\[\033[0m\033[0;32m\]\u\[\033[0;36m\] @ \[\033[0;36m\]\h \w\[\033[0;32m\]$git_status_command\n\[\033[0;32m\]└─\[\033[0m\033[0;32m\]\[\033[0m\033[0;36m\] ⟫\[\033[0m\] "

