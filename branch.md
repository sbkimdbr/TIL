### 상황 1. fast-foward

> fast-foward는 feature 브랜치 생성된 이후 master 브랜치에 변경 사항이 없는 상황

1. feature/test branch 생성 및 이동

   ```bash
   $ git checkout -b feature/test
   ```

   

2. 작업 완료 후 commit

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (feature/test)
   $ git commit -m 'complete test'
   [feature/test 1fc3dbb] complete test
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test.html
   ```
   
   


3. master 이동

   


4. master에 병합

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (master)
   $ git merge feature/test
   Updating 63bc818..1fc3dbb
   Fast-forward
    test.html | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test.html
   
   ```
   
   


5. 결과 -> fast-foward (단순히 HEAD를 이동)

   

6. branch 삭제

   

---

### 상황 2. merge commit

> 서로 다른 이력(commit)을 병합(merge)하는 과정에서 다른 파일이 수정되어 있는 상황
>
> git이 auto merging을 진행하고, commit이 발생된다.

1. feature/signout branch 생성 및 이동

   ```bash
   $ git checkout -b feature/signout branch
   ```

   

2. feature/signout branch 의 파일 생성과 작업 완료 후 commit

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (feature/signout)
   $ touch signout.html
   
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (feature/signout)
   $ git add .
   
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (feature/signout)
   $ git commit -m 'complete signout'
   //feature/signout 의 commit sign 은 'complete signout' 가 됨
   [feature/signout 8d29a5a] complete signout
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 signout.html
   
   ```

   

   

3. master 이동

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (feature/signout)
   $ git checkout master
   Switched to branch 'master'
   
   //명령을 내리는 사람이 master로 바뀐걸 확인 할 수 있다.
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (master)
   $ git log --oneline
   1fc3dbb (HEAD -> master) complete test
   63bc818 test2-commit
   a1fe886 (test) Init
   
   ```

   

4. *master에 추가 commit 이 발생시키기!!*

   * **다른 파일을 수정 혹은 생성하세요!**

   ```bash
   
   ```

   

5. master에 병합

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (master)
   $ git log --oneline
   ea3c871 (HEAD -> master) Merge branch 'feature/signout' into master
   6185785 hotfix
   8d29a5a (feature/signout) complete signout
   1fc3dbb complete test
   63bc818 test2-commit
   a1fe886 (test) Init
   
   ```

   

6. 결과 -> 자동으로 *merge commit 발생*

   * vim 편집기 화면이 나타납니다.

   * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력하여 저장 및 종료를 합니다.
      * `w` : write
      * `q` : quit
      
   * 커밋이  확인 해봅시다.

7. 그래프 확인하기

   

8. branch 삭제

   

---

### 상황 3. merge commit 충돌

> 서로 다른 이력(commit)을 병합(merge)하는 과정에서 동일 파일이 수정되어 있는 상황
>
> git이 auto merging을 하지 못하고, 해당 파일의 위치에 라벨링을 해준다.
>
> 원하는 형태의 코드로 직접 수정을 하고 merge commit을 발생 시켜야 한다.

1. feature/board branch 생성 및 이동

   ```bash
   user@DESKTOP-A1BNGSL MINGW64 ~/Desktop/branch (master)
   $ git checkout -b feature/board
   Switched to a new branch 'feature/board'
   ```

   

2. 작업 완료 후 commit

   


3. master 이동

   


4. *master에 추가 commit 이 발생시키기!!*

   * **동일 파일을 수정 혹은 생성하세요!**
   

   
5. master에 병합

   


6. 결과 -> *merge conflict발생*

   


7. 충돌 확인 및 해결

   


8. merge commit 진행

    ```bash
    $ git commit
    ```

   * vim 편집기 화면이 나타납니다.
   
   * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력하여 저장 및 종료를 합니다.
      * `w` : write
      * `q` : quit
      
   * 커밋이  확인 해봅시다.
   
9. 그래프 확인하기

    


10. branch 삭제




### Add  명령어 활용

```bash
//커밋 메세지 변경
$ touch c.txt
$ git add . -> commit 후
$ git commit --amend
vim 편집기에서 직접 메시지 수정 후 저장 

```



