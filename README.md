# Git cheat sheet

| git |  version 2.7.4 |
|-----|----------------|

### Basic git setup :


### Git config:
#### Set Global config:
##### These will be reflected as Author details in each commit you make
| Command | Description |
|---------|-------------|
| ` git config --global user.name "your_username"` | Auther |
| ` git config --global user.email "your_email"`	| Auther email |

| Command | Description |
|---------|-------------|
| ` git config --global core.editor "vim"` | Change editor to vim |
| ` git config --global core.ignorecase false`| Detect changes in filename case change |
| ` git config --global init.templatedir '~/.git_template` | Set git template dir ([to configre hooks][git-template-stackoverflow])|

#### Set Local config: ( modify config for current project)
| Command | Description |
|---------|-------------|
| ` git config  user.name "your_username"` | Auther |
| ` git config  user.email "your_email"`	| Auther email |
| ` git config core.ignorecase false`| Detect changes in filename case change |

#### Unset config:
| Command | Description |
|---------|-------------|
| ` git config --global --unset <config-key>` | Unset global config  <br>ex: git config --global --unset user.name |
| ` git config --unset <config-key>` | Unset local config  <br>ex: git config --unset user.name|

[More operations on config][git-config-stackoverflow]

### Adding git to project:
| Command | Description |
|---------|-------------|
| ` git init .` | Initialize git inside project root directory. |
| ` git add .` | Stage all files for commit. |
| ` git commit -m "commit-message"` | Commit staged files to git. |

### Adding Remote repo to Project:
| Command | Description |
|---------|-------------|
| ` git remote add <remote_name> <remote_address>` | Add remote repository where<br>remote_name: origin,upstream etc<br> remote_address:(url) gethub, bitbucket etc |
| ` git remote remove <remote_name>` |	Delete remote |
| ` git remote rename origin upstream` | Rename remote |
| ` git push <remote_name> <branch-name>` | Push all the commits to remote default branch name master |

### Synchronizing local with remote (upstream):
| Command | Description |
|---------|-------------|
| ` git fetch` | Download changes from remote without making any changes to files in the working directory. |
| ` git pull` | Download others commits from remote and apply to working directory. |
| ` git push` | Upload local commits to remote. |

### Branches in git:
| Command | Description |
|---------|-------------|
| ` git branch -a` | Show all branches. |
| ` git branch <new_branch_name> ` | Create new branch (Will not switch working tree to new branch). |
| ` git checkout -b <new_branch_name>` |Create new branch out of the current branch and switch to new branch. |
| ` git branch -m <old_branch_name> <new_branch_name>` | Rename branch. |
| ` git push <remote_name> <branch_name>` | Push local branch to remote. |
| ` git checkout <branch_name>` | Switch to specified branch. |
| ` git branch -d <branch_name>` | Delete local branch (replace -d by -D for force delete) |
| ` git push <remote_name> :<branch_name>` |Delete remote branch. |

### Git stash:
##### Save current changes without commiting before doing pull and checkout to other branch
###### Run following command after `git add <file>`
| Command | Description |
|---------|-------------|
| ` git stash save "message"` | Save chages with give message |
| ` git stash list` | Show list of stash |
| ` git stash apply stash@{n}` | Apply stashed file to the current branch without deleting from stash, where `n` is the stash number. |
| ` git stash pop` | Apply last stash to the current branch and delete stash |
| ` git stash clear` | Clear all stash |
| ` git checkout stash@{0} -- <filename>` | checkout file from last stash |
| ` git stash show -p` | view last stash content |
| ` git stash show -p stash@{1}` | view specific stash content |

### Commits in git:
| Command | Description |
|---------|-------------|
| ` git commit --amend` | Edit last commit message. |
| ` git revert <commit_id>` | Rollback to the commit specified by commit_id |
| ` git rebase -i HEAD~n` | Opens list of the last n commits,<br>replace _"pick"_ by _"reword"_ to alter the commit message of those commits. |
| ` git reset --soft HEAD~n`	| Uncommit last n commits without overwriting the working directory files. |
| ` git reset --hard HEAD~n`	| Uncommit last n changes and overwrite the working directory files |
| ` git cherry-pick <commit_id>` | Pull commit from any branch by its commit id into current branch |
| ` git rev-parse --short HEAD` | Print last commit id |
| ` git commit --all --amend`  | Add current changes to last commit |

### Merging in git :
| Command | Description |
|---------|-------------|
| ` git merge <branch_name>` | Merge any branch into current branch (creates merge commit) |
| ` git merge <branch-name> --no-commit` | Merge without any commit. |
| ` git pull <remote_name> <branch_name>` | Pull remote branch into local branch. On conflicts it will create merege commit |
| ` git checkout <branch_name> -- <file_name>` | Checkout single file from any branch |
| ` git checkout <branch_name> -- . | Checkout all the files from any branch |

### Fix diverged branches:
| Command |
|:-------:|
| `git rebase <remote_name>/<branch_name>` |
| or |
| `git rebase` |

### Caching in git :
##### Run these commands after updating gitignore then commit the changes.
| Command | Description |
|---------|-------------|
| `git rm --cached <filename>` | Remove specific file from git cache |
| `git rm -r --cached .` | Remove all files from git cache |

### Upstream in git :
##### Upstream is used when we have multiple repositories for single project
| Command | Description |
|---------|-------------|
| ` git branch --set-upstream-to=<remote_name>/<remote_branch_name> <local_branch_name>` | Set new upstream for the branch. |
| ` git push -u <remote_name> <branch_name>` | Push to remote branch and set as upstream |

### List commits in git (log):
| Command | Description |
|---------|-------------|
| ` git log` | List all commits. |
| ` git log -n` | The n is number of commits to list |


### Time savers
##### Edit last commit which is already pushed to remote.  
` git add . && git commit --amend --no-edit && git push --force`

### Tips:
#### Disable terminal screen (oh-my-zsh)
Add below line to `~/.zshrc` for permanent change.
```bash
unset LESS
```

### Reference:
---
[http://schacon.github.io/git/git.html](http://schacon.github.io/git/git.html)

[git-template-stackoverflow]: https://stackoverflow.com/questions/2293498/applying-a-git-post-commit-hook-to-all-current-and-future-repos
[git-config-stackoverflow]: https://stackoverflow.com/questions/11868447/how-can-i-remove-an-entry-in-global-configuration-with-git-config

