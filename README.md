# dotfiles

My Dotfiles using bare git repository: https://www.atlassian.com/git/tutorials/dotfiles

## Usage Instructions
On a new machine, to setup dotfiles do the following:

1. Clone dotfiles repo to home directory
```
   git clone --bare https://github.com/akamsali/dotfiles.git $HOME/dotfiles 
```

2. Execute the following commands: 
```
   alias config='git --git-dir=$HOME/dotfiles/ --work-tree=$HOME'
   echo "dotfiles" >> .gitignore
   mkdir -p .config-backup && \
     config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
     xargs -I{} mv {} .config-backup/{}
   config checkout
   config config --local status.showUntrackedFiles no
```

