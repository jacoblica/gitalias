# gitalias.sh

A really cut down the key-strokes git alias script.

## Full list

```bash
# =========== Git alias ============
# Git stash
alias gs='git stash'
alias gsp='git stash pop'
alias gp='git push'

# Git log
alias gl='git log --reverse'
alias gll='gl -20'
alias gl2='git log --reverse --pretty=format:"'"%C(auto,yellow)%h %C(auto,red)%ad %C(auto,reset)%s %C(auto,magenta)(%an)"'" --date=short'
alias gl='git log --reverse --pretty=format:"'"%C(auto,yellow)%>(18,trunc)(%an) %C(auto,magenta)%h %C(auto,cyan)%ad %C(auto,reset)%s "'" --date=short'
alias gl1='git log --graph --pretty=format:"'"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset"'" --abbrev-commit'
alias gl3='git log --graph --pretty=format:"'"%C(yellow)%>(60,trunc)%d%Creset - %C(bold blue)%>(18,trunc)(%an)%Creset %Cred%h%Creset - %s %Cgreen(%cr) %Creset"'" --abbrev-commit'
alias log='git log --reverse --oneline --graph --decorate --color=always'

# Git grep
alias gg='git grep'

# Git branch
alias gb='git branch -vv --color=always' #lists all branches with latest commits
alias gbd='git branch -D'
alias gba='git branch -a'
alias gbr='git branch -r'
alias gbc='git branch --contains' # give commit sha, and find which branch it is in.

# Git fetch
alias gfa='git fetch --all'

# Git checkout
alias gc='git checkout'
alias gcf='git checkout -f'  # This is used to throw away local changes
alias gcd='git checkout develop'
alias gcb='git checkout -b' #causes a new branch to be created

alias grv='git remote -v'  # Show remote origin
alias grr='git remote rm'

alias gpu='git pull'
alias gcl='git clone'

# Git Status
alias g='git status -sb'
alias gs='git status -sb'

# Git Diff
alias gd='git difftool' # Using icdiff tool, working directory (uncommitted modifications) and "last version" is HEAD
alias gdo='git diff' #
alias gsh='git show' # show changes of the commits
alias glp='git log --reverse -p'
alias gd1='git diff HEAD^ HEAD' # diff the last commit  with the 1th previous commit
alias gd2='git diff HEAD~2 HEAD' # diff the last commit  with the 2nd previous commit
alias gdc='git diff --cached' #shows staged changes.
alias gdp='git diff --no-prefix' # Output patch compatible diff format
alias gt='git tag'

# Git add and remove
alias ga='git add'
alias gaa='git add -u' # Add all modified files
alias gr='git rm'

# Git commit
alias gcm='git commit -m'
alias gca='git commit --amend'
alias gcn='git commit --no-verify -m'        # bypasses the pre-commit and commit-msg hooks. https://stackoverflow.com/questions/7230820/skip-git-commit-hooks

# Git Rebase
alias grm='git rebase master'
alias grom='git rebase origin/master'
alias grod='git rebase origin/develop'
alias gra='git rebase --abort'
alias grc='git rebase --continue'
alias grs='git rebase --skip'
alias gri='git rebase -i'
alias grir='git rebase -i --root'      # Rebase the first two commits in Git repository(when there are only two commits)

# Git push your changes
alias gpob='echo ">> Push local branch $(git rev-parse --abbrev-ref HEAD) to stash"; sleep 3; git push origin $(git rev-parse --abbrev-ref HEAD) --force'
# Git delete last commit from the local repo
alias gcmdelete='git reset --hard HEAD~1'     # --hard: see nothing when git status, uncommit + unstage + delete changes, nothing left.
alias gcmyellow='git reset --mixed HEAD~1'    # --mixed (default):see yellow when git status, uncommit + unstage changes, changes are left in working tree.
alias gcmgreen='git reset --soft HEAD~1'      # --soft: see green when git status, uncommit changes, changes are left staged (index).
alias guadd='git reset'                       # undo git add, the same as (git reset --mixed HEAD~0), use it when git status shows green(means in index)
# https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard
# https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified

# Git clean
alias gci='git clean -i'
alias gcs='git clean -n' # show what will be deleted
alias gcforce='git clean -f' # delete files:
alias gcfd='git clean -fd'    # Remove untracked files and folders
alias gurl='git config --get remote.origin.url'

# Others
alias gls='git ls-files -s '              # Show staged contents' mode bits, object name and stage number in the output.
alias gux='git update-index --chmod=+x '  # Add X permission to a file. git add --chmod=+x path/to/file since Git 2.9

# Patch management
alias patchcreate='git diff --no-prefix ' # https://gist.github.com/zeuxisoo/980174
alias patchapply='patch -p0 ' # http://nithinbekal.com/posts/git-patch/
# =========== Prompt ===========


```

## Installation

- download script
```bash
  mkdir ~/.gitalias
  curl https://raw.githubusercontent.com/jacoblica/gitalias/master/gitalias.sh > ~/.gitalias/aligitaliasasme.sh
```
- add alias to your startup script (ex: ~/.bash_profile, ~/.bashrc)
```bash
echo "source ~/.gitalias/gitalias.sh" >> ~/.bash_profile
```

## License
The module is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).