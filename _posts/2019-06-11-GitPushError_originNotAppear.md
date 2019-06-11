---
layout: post
title: Git push 에러 “fatal: 'origin' does not appear to be a git repository”
category: Git
tags: [Git]
---

<br>
<br>
아래와 같이 git push를 요청하는데 아래와 같은 에러 메시지가 나타난다.<br>
```{.no-highlight}
$ git push origin master
```
 * 에러 메시지
```{.no-highlight}
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.
```
<br>
일단 'origin'이 없다하니 아래 명령어를 통해 내가 입력한 리모트 저장소의 단축 이름 확인해보자.<br>
<br>
### git remote 
 - 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있으며, 리모트 저장소의 단축 이름을 보여준다. <br>
 - `-v` 옵션을 주어 단축이름과 URL을 함께 볼 수 있다. <br>
 - 저장소를 Clone시 `origin`이라는 리모트 저장소가 자동으로 등록되기 때문에 `origin`이라는 이름을 볼 수 있다.<br>
<br>
<br>
```{.no-highlight}
$ git remote -v
```
위 명령어 입력 결과, 아래와 같이 나타나는데<br>
```{.no-highlight}
origin  https://github.com/sykim-ivy/java-algorithm-basic.git (fetch)
origin  https://github.com/sykim-ivy/java-algorithm-basic.git (push)
```


'origin'이 없다 정말 'origin'을 'orgin'으로 잘못 기입한 문제였다 ㅎㅎ;<br>
<br><br>

### Git에서 'orgin'이란?? 
궁금해져서 찾아보니 `원격 저장소 URL의 단축 alias`라고 한다.<br>
 * 친절한 stackoverflow 답변 
 > It is rather a local alias set as a key in place of the remote repository URL.<br>
<br>
<br>
### remote 별칭 변경
간혹 정말 orgin이 등록 안되는 경우도 있지만 내경우 등록명을 잘못 등록한 것이니 수정하면 빠르게 해결하였다<br>
아래 명령어를 통해 orgin을 orgin으로 변경해주니 push가 잘 된다! :-)<br>
```{.no-highlight}
$ git remote rename orgin origin
```
```{.no-highlight}
$ git remote rename <기존단축이름> <변경단축이름>
```
<br><br>

### 로컬경로에 원격 저장소를 추가 & remote 별칭 생성
```{.no-highlight}
$ git remote add <단축이름> <url>
```
 - `git clone` 명령은 묵시적으로 origin 리모트 저장소를 어떻게 추가
<br><br>
 * Example
```{.no-highlight}
$ git remote
origin
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
pb	https://github.com/paulboone/ticgit (fetch)
pb	https://github.com/paulboone/ticgit (push)
```
<br>
<br>
git도 공부해야할 게 많다 ㅎㅎㅎ
<br><br><br>

## Refs
[Git push error: “origin does not appear to be a git repository”] (https://stackoverflow.com/a/15445062)
[What is “origin” in Git?] (https://stackoverflow.com/questions/9529497/what-is-origin-in-git)
[2.5 Git의 기초 - 리모트 저장소] (https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C)

