# 마크다운 문법

## 제목(heading)

제목은 `#` 으로 표현한다. 제목의 레벨은 `#`의 갯수로 표현되며 , h1~h6까지 표현 가능하다.

### 제목3

#### 제목4

##### 제목5

###### 제목6

## 목록

목록은 순서가 있는 목록과 순서가 없는 목록으로 구분된다.

1. 순서가 있는 목록

2. 순서가 있는 목록

   1.tab을 통해 하위 목록으로 진입

   2.계속 작성

  3.shift
* 순서가 없는 목록
  * tab 치면 하얀점이 나온다
  * 엔터치면 그대로 내려온다
* 엔터 단계별로 치면 돌아간다

# 코드블럭

```html
<h1>
    html 코드
</h1>
```

```sql
SELECT * FROM tables;
```

```bash
$git init
```

다양한 프로그래밍 언어 문법의 syntax highliting을 지원한다.

## 링크

[구글 링크 (https://google.com)]



## 이미지



![11](md-images/11.jpg)

* 설정 > copy imgage to custom 
  * 환경설정



# 표

| 번호 |      |      |
| ---- | ---- | ---- |
| 1    |      |      |
| 2    |      |      |
| 3    |      |      |



# 기타

**굵게**

*기울임*

~~취소선~~ (앞뒤 ~~)

--- 하이픈 세개

~~~이건뭐야~~~
오잉
~~~

~~~~~

~~~~~

# Git

> Git - 분산형 버전 관리 시스템 (DVCS) 중 하나이다.

## Git 사전 준비

> git을 사용하기 전에 커밋을 남기는 사람에 대한 정보를 설정(최초)

```bash
$ git config --global user.name 'sbkimdbr'
$ git config --global user.email 'sbkimdbr@gmail.com'
```

* 추후에 커밋을 하면 , 작성한 사람으로 저장된다

* email은 github 등록 이메일로 

* 설정 내용을 확인하기 위해서는 아래 명령어

  ```bash
  $ git config --global -l
  user.email=sbkimdbr@gmail.com
  user.name=sbkimdbr
  ```

git bash 설치링크  [git bash]( )

# 기초흐름

```bash
$ git init
Initialized empty Git repository in C:/Users/user/Desktop/test2/.git/
```

* git 저장소를 만들게 되면 해당 디렉토리 내
* git bash에서는  `.git/` 폴더 생성
* git bash에서는 `(master)`로 현재 작업중인 브랜치 표시

### 1. `add`

> 커밋위한 파일 목록

```bash
$ git add .         # 현재 디렉토리의 모든 파일 및 폴더
$ git status
#마스터 브랜치에 있다
On branch master
No commits yet
#아직 커밋안된 상태의 파일들이 있다.
Changes to be committed:
   #unstage 하기위해서
   #working directory 단계로 내리고 싶으면 " "의 구문 사용
  (use "git rm --cached <file>..." to unstage)
        
        new file:   a.txt
  #트래킹 안됨
  #git으로 관리 안함
  #working directory
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

$ git add a.txt     # 특정파일
$ git add md-images # 특정폴더
```

### 2.`commit`

> 버전 기록

```bash
$ git commit -m 'commit ok'
[master (root-commit) 3d97393] commit ok
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
 create mode 100644 b.txt

```

* 커밋 메세지는 현재 버전을 알 수 있도록 명확하게 작성
* 커밋 이력을 남기기 확인하기 위해서는 아래의 명령어 입력

```bash
$ git log
$ git log -l # 최근 한개의 버전
$ git log  --oneline
fatal: ambiguous argument 'line': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'

$ git log -l --oneline
```

### Status - 상태확인

> git 에 대한 상태 확인

```bash
##작업하면 add하고 commit 한다
```



* Staging area ? add, commit ??

- a.sql , b.java 파일을 만들었다
- 버전 따로 기록
  - 디비작업
  - 스프링코드

```bash
$ git add a.sql
$ git commit -m 'db commit ok'
$ git add b.java
$ git commit -m 'java commit ok'   #파일 따로 커밋
$ git add SPRING/ 
$ git commit -m '스프링코드'         #폴더 커밋 
```



```bash

```



## 원격 저장소 활용하기

> 원격 저장소 제공하는 서비스는 github,gitlab,bitbucket이 있다

## 1.원격저장소 설정

```bash
$ git remote add origin https://github.com/sbkimdbr/git-test.git
```

- 깃아 , 원격 저장소로 추가해줘 origin 이라는 이름으로 url을 

### 2. 원격저장소 확인하기

```bash
$ git remote -v
origin  https://github.com/sbkimdbr/git-test.git (fetch)
origin  https://github.com/sbkimdbr/git-test.git (push)
```

### 3. push

```bash
$ git push origin master
Everything up-to-date
```



> ex) remote.txt 파일 만들고 push 까지 해보기



#### working ,stacking area , commit version , version upload 구분하기

###### 1. working area

``` bash
user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/test2 (master)
$ touch complete.txt
user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/test2 (master)
$ touch non-com.txt

```







