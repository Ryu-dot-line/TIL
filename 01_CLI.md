# CLI

Command Line Interface

- Command(명령어)를 통해 작동하는 인터페이스

  <-> GUI(Graphic User Interface)



## 기초 명령어

### (1) `pwd`

- `pwd` : Print Working Directory (현재 폴더의 경로)

- `~` (home directory) : 홈 디렉토리(git bash를 처음 열면 기본 디렉토리)



### (2) `ls`

- `ls`(list) : 현재 위치의 내용물 출력(list)



### (3) `cd [폴더명]`

- `cd` (Change Directory) : 폴더 변경
- `cd ..` : 상위 폴더로 이동
- `cd .` : 현재 폴더로 이동



### (4) `mkdir [폴더명]`

- `mkdir`(make directory) : 폴더 생성



### (5) `rm [파일]`

- `rm`(remove) : 파일 삭제
  - 예 : 복수개의 파일 삭제

```shell
$ rm a.txt b.txt
```



### (6) `rm -r [폴더명]`

- `-r` (recursively) : 재귀적으로 폴더 삭제



### (7) `touch [파일명]`

- `touch` : 파일 생성



### (8) `cp [파일명] [위치]`

- `cp`(copy) : 파일 복사
  - 예 : a.txt 파일을 복사 -> 같은 폴더의 b.txt 파일 생성

```shell
$ cp a.txt ./b.txt
```



### (9) `cp -r [폴더명] [위치]`

- `cp -r` : 폴더 복사



### (10) `mv [파일/폴더명] [변경할 파일/폴더명]`

- `mv` (move) : 파일/폴더명 변경
  - 예 : a.txt -> b.txt 파일명 변경, a -> b 폴더로 이동

```shell
$ mv a.txt b.txt
```



- `mv [파일/폴더명] [경로]` : 파일/폴더를 해당 경로로 이동
  - 예 : b.txt -> bb 폴더로 경로 이동

```shell
$ mv b.txt bb
```

