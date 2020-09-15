# Git

Source Code Management(SCM) : 코드 관리 도구(버전을 통해 관리)

Version Control System(VCS) : 버전 컨트롤 시스템

local computer 상의 파일 버전 관리

- 인터넷 연결과 무관
- 인터넷/원격 서버에서 관리 하기 위해서는 `git hub` 필요

`폴더` 단위로 버전 관리



## 주요 사항

### (1) `git`  폴더 기준으로 프로젝트(코드) 관리



### (2) `git init`

- 현재 폴더에서 코드 관리 시작 
  - 루트 폴더 뒤에 `(master)`라고 붙음
- `.git` 폴더 생성 == git으로 폴더가 관리되어 있음
- `.git` 폴더 삭제 == git으로 폴더를 관리하지 않겠다.
- 현재 폴더가 git으로 관리되고 있는지 확인
  - .git 폴더가 있는가
  -  폴더 명 뒤에 `(master)` 붙음



### (3) `git status ` 

- 현재 상태 출력(status) 

```shell
$ git status

On branch master 	// 마스터 브랜치에 있음
No commits yet 		// 아직 commit 없음
nothing to commit (create/copy files and use "git add" to track)	// commit 할게 없음
```



- 새로운 파일이 생성된 경우

```shell
$ git status

On branch master
No commits yet

Untracked files:		// 추적하고 있지 않음
  (use "git add <file>..." to include in what will be committed)
        a.txt		// 추가된 파일
        
nothing added to commit but untracked files present (use "git add" to track)
```



- git add 한 경우

```shell
$ git status

On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```



- 버전 관리 중인 파일이 수정된 경우

```shell
$ git status
On branch master
Changes not staged for commit:	// commit하기 위해 변화들이 stage에 추가되지 않았다.
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt		// 수정 발생한 파일

no changes added to commit (use "git add" and/or "git commit -a")
```



### (4) `git add [파일명]`

- `버전을 만들/commit할/스냅샷을 찍을` 파일 추가
- git add 이후 git status

```shell
$ git status

On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```



### (5) `git commit -m ["버전명"] `

- commit 및 버전명
- `git commit -m` : git commit 시, message와 함께
- commit 후 commit status

```shell
$ git status
On branch master
nothing to commit, working tree clean	// working tree(현재 폴더)가 클린하다 commit해야할 것도 없다
```



###  (6) 사용자 정보 config

- `git config --global user.email ["이메일주소"]`
- `git config --global user.name ["사용자명"]`



### (7) `git log`

- git commit 이력 확인

```shell
$ git log
commit 59b2d89081c56d05eb157c92f789b9d2c09b6313 (HEAD -> master)
Author: HJ Ryu <rhj2594@gmai.com>
Date:   Tue Sep 15 15:21:31 2020 +0900

    Add World to a.txt

commit fcc302724d603e16003333bbd4bb5bbeab7e9ff8
Author: HJ Ryu <rhj2594@gmai.com>
Date:   Tue Sep 15 15:15:07 2020 +0900

    Modify a.txt

commit d4393df37937a0cb78008169e32906a5f4b2b093
Author: HJ Ryu <rhj2594@gmai.com>
Date:   Tue Sep 15 14:50:59 2020 +0900

    First Commit

```



- `git log --oneline` : git log 한줄로 확인

```shell
$ git log --oneline
59b2d89 (HEAD -> master) Add World to a.txt
fcc3027 Modify a.txt
d4393df First Commit
```



### (8) `git checkout [버전명]`

- 버전명 상태로 돌아감

```shell
$ git checkout d4393df
Note: switching to 'd4393df'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at d4393df First Commit

ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git ((d4393df...))	// d4393df 버전으로 돌아감
```



- `git checkout master` : 최신 버전으로 돌아감

```shell
ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git ((d4393df...))
$ git checkout master
Previous HEAD position was d4393df First Commit
Switched to branch 'master'

ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git (master)	/// 최신 버전(master)으로 돌아감
```





---

## 반복 작업

### (1) 기존 파일에 내용 추가

- a.txt 파일에 "hello"라는 내용 추가



### (2) git status 확인

```shell
$ git status
On branch master
Changes not staged for commit:	
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
```



### (3) git add

```shell
$ git add a.txt
```



### (4) git status

```shell
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   a.txt
```



### (5) git commit

```shell
$ git commit -m "Modify a.txt"
[master fcc3027] Modify a.txt
 1 file changed, 1 insertion(+)
```



### (6) git log

```shell
$ git log
commit fcc302724d603e16003333bbd4bb5bbeab7e9ff8 (HEAD -> master)
Author: HJ Ryu <rhj2594@gmai.com>
Date:   Tue Sep 15 15:15:07 2020 +0900

    Modify a.txt

commit d4393df37937a0cb78008169e32906a5f4b2b093
Author: HJ Ryu <rhj2594@gmai.com>
Date:   Tue Sep 15 14:50:59 2020 +0900

    First Commit
```



---

# git hub(원격 저장소)

### (1) `git remote add [저장소의 이름][저장소의 URL]`

- local의 git과 git hub 연결
- 저장소의 이름 : `origin`
  - 암묵적으로 첫번째 저장소의 이름은 `origin`

```shell
$ git remote add origin https://github.com/Ryu-dot-line/TIL.git
```



### (2) `git remote -v`

- 원격 저장소(git hub) 정보 출력
  - git remote : 간략 
  - git remote -v : 상세 

```shell
$ git remote
origin

$ git remote -v
origin  https://github.com/Ryu-dot-line/TIL.git (fetch)
origin  https://github.com/Ryu-dot-line/TIL.git (push)
```



### (3) `git push [저장소명][브랜치명]`

- origin이라는 저장소에 master 브랜치 업로드

```shell
$ git push origin master
```





