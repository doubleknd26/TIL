# git stash 란 무엇인가?

git stash란, commit을 하지 않고도, 현재 작업 중인 브랜치의 변경 사항을 저장할 수 있는 방법이다. 다음과 같은 경우를 생각해보자.

## 상황
브랜치 A에서 작업을 하다가, 갑자기 브랜치 B에서 작업을 해야하는 경우, 브랜치 A에서 작업했던 변경 사항들을 어떻게 할 것인가

## 방법
1. 임시로 commit 했다가, reset 한다.
2. git stash 를 사용한다.


## git stash 사용법
```bash

# apply git stash
git stash 

git stash save "description" # add description is more readable.


# re-apply
git stash apply # get changes and keep it in the stash

git stash pop   # get changes and remove it from the stash
```

기본적으로 `git stash` 는 untracked files 과 ignored file 들을 stash에 저장하지 않는다. 이를 저장하게 하려면 다음 명령어를 사용해야 한다.
```bash
git stash -u (or --include-untracked) # save untracked files

git stash -a (or --all) # save all changes including ignored files.
```


## multiple git stash
```bash
$ git stash list
stash@{0}: On master: create t3 # git statsh save "create t3"
stash@{1}: WIP on master: 08a97f0 init
```

`git stash pop` 은 기본적으로 가장 최신의 stash ( stash@{0} ) 를 pop 한다. 만약 특정 stash를 pop 하고 싶다면, 아래와 같이 하면 된다.
```bash
$ git stash pop stash@{1}

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   t2

Dropped stash@{1} (ac9f1cfcb508340432db0a48379cb8eab57d5f4e)
```

## stash 삭제
```bash
$ git stash drop stash@{0} # drop specific stash
Dropped stash@{0} (e89913bb949a0064dee8b3625b84d6b1205ddb09)

git stash clear # remove all stash
```


*refercence:*  
*- https://www.atlassian.com/git/tutorials/saving-changes/git-stash*