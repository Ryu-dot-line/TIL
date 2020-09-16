# Git

- Source Code Management(SCM) : 코드 관리 도구(버전을 통해 관리)

- Version Control System(VCS) : 버전 컨트롤 시스템

- local computer 상의 파일 버전 관리
  - 인터넷 연결과 무관
  - 원격 서버에서 관리 하기 위해서는 `git hub` 등 필요

- `폴더` 기준으로 프로젝트(코드) 관리



# Git 세팅 : Local

### (1) Git으로 프로젝트 관리 시작 : `git init`

- `git bash`에서 프로젝트 시작 폴더로 이동 후 아래의 명령어로 `git` 관리 시작
  - 현재 폴더에서 코드 관리 시작 
  - 루트 폴더 뒤에 `(master)`라고 붙음

```shell
$ git init
```



- `.git` 폴더 생성 == git으로 폴더가 관리되어 있음
- `.git` 폴더 삭제 == git으로 폴더를 관리하지 않겠다.



- 현재 폴더가 git으로 관리되고 있는지 확인 방법
  - .git 폴더가 있는가
  -  폴더 명 뒤에 `(master)` 붙음



### (2) 현재 Git의 상태 조회 : `git status ` 

- 현재 상태 출력

```shell
$ git status
```



- commit 사항 없을 때 

```shell
$ git status

On branch master 	# 마스터 브랜치에 있음
No commits yet 		# 아직 commit 없음
nothing to commit (create/copy files and use "git add" to track)	# commit 할 게 없음
```



- 새로운 파일이 생성된 경우

```shell
$ git status

On branch master
No commits yet

Untracked files:		# 추적하고 있지 않음
  (use "git add <file>..." to include in what will be committed)
        a.txt		# 추가된 파일
        
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



### (2) Commit을 위한 Staging : `git add [파일명]`

- 현재 코드 상태의 스냅샷을 찍기 위한 파일 선택(== Staging Area에 파일 추가)
  - `버전을 만들/commit할/스냅샷을 찍을` 파일 선택

```shell
$ git add [파일 이름] # .은 모든 변경 사항을 staging area로 올림
```



- git add 이후 git status

```shell
$ git status

On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```



### (3) 버전 관리를 위한 스냅샷 저장 :  `git commit -m ["커밋 메시지"] `

- 현재 상태에 대한 스냅샷 `commit`하여, 버전 관리 진행
- `git commit -m` : git commit 시, message와 함께 커밋

```shell
$ git commit -m "커밋 메시지"
```



- commit 후 commit status

```shell
$ git status
On branch master
nothing to commit, working tree clean	# working tree(현재 폴더)가 클린, commit해야할 것도 없다
```



###  (4) 사용자 정보 

- 사용자의 email, name 설정 
  - 사용자 email/name 변경시에도 동일한 코드로 변경

```shell
$ git config --global user.email ["이메일주소"]
$ git config --global user.name ["사용자명"]
```



# Git 버전 관리 : Local

### (1) `git log`

- 버전 관리 이력 조회

```shell
$ git log
```



- `git log` : 버전 관리 이력 상세 조회

```shell
$ git log
commit 59b2d89081c56d05eb157c92f789b9d2c09b6313 (HEAD -> master)
Author: HJ Ryu <*@gmail.com>
Date:   Tue Sep 15 15:21:31 2020 +0900

    Add World to a.txt

commit fcc302724d603e16003333bbd4bb5bbeab7e9ff8
Author: HJ Ryu <*@gmail.com>
Date:   Tue Sep 15 15:15:07 2020 +0900

    Modify a.txt

commit d4393df37937a0cb78008169e32906a5f4b2b093
Author: HJ Ryu <*@gmail.com>
Date:   Tue Sep 15 14:50:59 2020 +0900

    First Commit

```



- `git log --oneline` : 버전 관리 이력 한줄 조회

```shell
$ git log --oneline
59b2d89 (HEAD -> master) Add World to a.txt
fcc3027 Modify a.txt
d4393df First Commit
```



### (2) `git checkout [버전명]`

- [버전명] 상태로 돌아감

```shell
$ git checkout [버전명]
```



- `git checkout [d4393df]` : d4393df 버전으로 돌아감

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

ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git ((d4393df...))	# d4393df 버전으로 돌아감
```



- `git checkout master` : 최신 버전으로 돌아감

```shell
ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git ((d4393df...))
$ git checkout master
Previous HEAD position was d4393df First Commit
Switched to branch 'master'

ial10@LAPTOP-7DD8I63A MINGW64 ~/basic_git (master)	# 최신 버전(master)으로 돌아감
```



---

# Github 세팅 : 원격 저장소

### (1) 원격 저장소 정보 추가 : `git remote add [저장소의 이름][저장소의 URL]`

- local의 Git과 Github 원격(remote) 저장소(repository)를 생성하고 현재 폴더와 연결	
  - local 저장소는 `git init`이 된 상태
  - 원격 저장소에 새로운 repository가 생성된 상태
- 저장소의 이름 : `origin`
  - 암묵적으로 첫번째 저장소의 이름은 `origin`

```shell
$ git remote add origin https://github.com/Ryu-dot-line/TIL.git
```



### (2) 원격 저장소 정보 조회 : `git remote -v`

- 원격 저장소(git hub) 정보 조회
  - git remote : 간략 
  - git remote -v : 상세 

```shell
$ git remote
origin

$ git remote -v
origin  https://github.com/Ryu-dot-line/TIL.git (fetch)
origin  https://github.com/Ryu-dot-line/TIL.git (push)
```



# 버전관리 : Local(Git) -> 원격 저장소(Github)

### (1) 원격 저장소로 코드 밀어넣음 : `git push[저장소명][브랜치명]`

- Git -> Github 원격 저장소에 push

```shell
$ git push origin master
```



### (2) 순서

###  `add`|`rm` -> `commit` -> `push`

```shell
$ git add README.md
$ git commit -m "add README.md"
$ git push origin master
```



### (3) 저장소 정보 삭제 : `git remote remove [저장소명]`



### (4) 파일 이름을 수정하거나, 삭제했을 때

- `git add -u` : `git add` 없어진 파일이나 이름이 바뀐 파일을 인식하지 못하기 때문에, 수정(update)된 파일들을 추가하고 싶을 경우 사용한다.
- `git add .` : 현재 폴더 내부의 모든 변화를 state에 추가한다.

### (5) 파일 삭제 : `git rm `

- Local(Git)과 원격저장소(Github) 에서 파일 삭제

```shell
$ git rm [파일명]
```



- 원격저장소(Github)에서만 파일 삭제(Local(Git)에서는 파일 삭제하지 않음)

```shell
$ git rm --cached [파일명]
```



---



# 원격관리 : 원격 저장소(Github) -> Local(Git)

### (1)  원격저장소에서 `처음`으로 프로젝트 복제할 때 : `git clone [원격 저장소의 주소]`

```shell
$ git clone https://github.com/Ryu-dot-line/TIL.git

# 완료 메시지
Cloning into 'TIL'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (24/24), done.
remote: Total 30 (delta 11), reused 23 (delta 4), pack-reused 0
Unpacking objects: 100% (30/30), 10.62 KiB | 159.00 KiB/s, done.
```

- clone 받은 repository에서는 remote를 설정하지 않아도 원격저장소가 연결된다.

### (2) 원격저장소에서 프로젝트 상의 변경사항 내려 받을  때 : `git pull [저장소명] [브랜치명]`

```shell
$ git pull origin master

# 완료 메시지
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), 247 bytes | 35.00 KiB/s, done.
From https://github.com/Ryu-dot-line/TIL
 * branch            master     -> FETCH_HEAD
   d3ea488..d6c89f4  master     -> origin/master
Updating d3ea488..d6c89f4
Fast-forward
 django.md | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 django.md
```



---



# 파일 변경 사항 확인

### (1) 파일 변경 사항 확인 : `git diff [파일명]`

```shell
$ git diff READM.md

# 변경 사항 있을 경우 출력됨
diff --git a/README.md b/README.md
index c06601f..3452f05 100644
--- a/README.md
+++ b/README.md
@@ -1,5 +1,5 @@
 # 백일장
-다음 제시어로 n행시를 완성하세요.
+다음 제시어로 n행시를 완성하세요~!

 ## 제시어
 - 사: 사차산업은
```



---



# 기타 

### (1) VS Code Open

```shell
$ code .   # 현재 폴더의 파일 VS Code에서 열기
$ code ..  # 상위 폴더의 파일 VS Code에서 열기
```

