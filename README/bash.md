# .bash_profile 환경설정

```.bash_profile
#alias로 단축명령 설정
alias cls='clear'

#NVM 설정
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# 프롬프트에서 Git 브랜치명 보기
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u:\w\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
```