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
    # remove `--global`, to set this repo only
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
> git reset {sha1/HEAD~/HEAD^100}  
> usually when pull required after commit, use `git reset --soft HEAD^`
    
| options |    how   |   what for|
|:--------|:--------:|----------:|
|--soft   |This leaves all your changed files "Changes to be committed"|打多个版本的PATCH|
|--mixed  |the changed files are preserved but not marked for commit(default action)|重新提交|
|--hard   |Any changes to tracked files in the working tree since <commit> are discarded|完全恢复到某版本|
|--merge  |Resets the index and updates the files in the working tree that are different between <commit> and HEAD and keep unstaged changes|恢复至某版本，并保留未提交的(检测有没有修改冲突)|
|--keep   |HARD and If a file that is different between <commit> and HEAD has local changes, reset is aborted|HARD&&检测有没有修改冲突|


### branch
#### create
    git branch test ${commit}
#### switch
    git checkout master
#### create && switch
    git checkout -b dev
#### merge
    git merge dev 
#### merge remote branch ==> update_local,push_remote
    # sync dev
    git fetch origin dev
    git pull origin/dev
    # if conflicts
    # fix and commit
    # merge dev to master
    git checkout master
    git merge dev
    git push
#### delete
    # delete remote
    git branch -r -d  origin/patch-2
    git push origin :patch-2
    # then checkout other branch, 
    # delete local
    git branch -d dev

#### list
    # local
    git branch
    # remote
    git branch -r
#### push 
    # create if remote not exists
    git push -u origin/<分支> dev
#### pull
```
  ~~# if remote exists
    git branch --set-upstream-to=origin/<分支> dev
    git pull
    # o
    git fetch
    # update
    # 无效X
    # git config --global core.mergeoptions --no-edit
    # 将会新加mergeX
    git pull --no-edit
    # stashX before commit
    git stash
    git pull --no-edit
    git stash pop stash@{0}
    # fetch
    # see how to deal with conflict
    git fetch~~
```
    # ~= git `rebase`
    git pull -ff-only origin develop
    # conflict
    ## local changed
    git stash save -a 'msg'# the first one, as it use stack
    git pull -ff-only origin develop
    ## recovery
    git stash pop
    ## commit/stash conflict
    ## reset/commit

### tag
    git checkout -b tags
    git push -u origin tags
    git tag tags_version
    git tag
    git push origin tags_version|--tags
    git tag -d tags_version
 
### repush(rollback && commit)
    # https://blog.csdn.net/fuchaosz/article/details/52170105
    # 1. new commit to overwrite ~= new commit
    # pass
    # 2. rollback
    # rollback local
    git reset --soft HEAD^
    # recommit
    git commit -m "xxx"
    # push -f
    git push -f
    # tell others or if you in you own branch
 
### [merging-an-upstream-repository-into-your-fork](https://help.github.com/articles/merging-an-upstream-repository-into-your-fork/)
    # if not conflict
    # local master
    git pull https://github.com/scrapy/scrapy.git master
    git push
    git checkout patch-2
    git reset HEAD^
    git stash
    git pull --ff-only origin master
    git stash pop
    git commit -m "add item_error to be catchable"
    git push -f
    
    # if conflict, just merge
    # local patch-2
    git pull https://github.com/scrapy/scrapy.git master
    # solve and commit and push

    
    

[1]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000
