# LEARN GIT
- markdown: https://daringfireball.net/projects/markdown/dingus
- ref from: [GIT 教程][1].

## python with git
> https://github.com/libgit2/pygit2/tree/master/pygit2 # with libgit2  
  https://github.com/gitpython-developers/GitPython # with subprocess of git  
  https://pypi.python.org/pypi/dulwich # maybe still in dev && no source available  

## local
    git init

## remote

### ssh
> about ssh.pub ref: ssh_config(5)
### whoami
    git config --global user.email "1258626769qq.com"
    git config --global user.name "chainly"
### clone
    git clone git@github.com:chainly/learn_git.git
### push
    git remote add origin git@github.com:chainly/learn_git.git
    git add learn_git.md
    git commit -m 'add learn_git.md'
    git push -u origin master

### info
    git status
    git diff `${file}`
    git log
    git reflog
### [reset](https://git-scm.com/docs/git-reset#git-reset-emgitresetemltmodegtltcommitgt) 
    git reset {sha1/HEAD~/HEAD^100}
| options |    how   |   what for|
|:--------|:--------:|----------:|
|--soft   |This leaves all your changed files "Changes to be committed"|打多个版本的PATCH|
|--mixed  |the changed files are preserved but not marked for commit(default action)|重新提交|
|--hard   |Any changes to tracked files in the working tree since <commit> are discarded|完全恢复到某版本|
|--merge  |Resets the index and updates the files in the working tree that are different between <commit> and HEAD and keep unstaged changes|恢复至某版本，并保留未提交的(检测有没有修改冲突)|
|--keep   |HARD and If a file that is different between <commit> and HEAD has local changes, reset is aborted|HARD&&检测有没有修改冲突|


[1]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000
