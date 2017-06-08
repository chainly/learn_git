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

## info


[1]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000
