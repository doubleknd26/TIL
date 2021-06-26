# How to merge reverted commit


```bash
$ git log --pretty=oneline --graph
* 0b44e7340409420aeae064e3f784fd2636980252 (HEAD -> master) add t1 file

$ ll
t1
```

```
git revert {reverted commit}
git commit
git push
```


```


![alt text](https://github.com/doubleknd26/TIL/blob/main/images/git_1.png?raw=true)

https://github.com/doubleknd26/TIL/blob/main/images/git_1.png



https://github.com/doubleknd26/TIL/blob/main/images/git_1.png?raw=true