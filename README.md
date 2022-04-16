### License
Sesame is Free software, and may be redistributed under the terms of specified in the [LICENSE]() file.

오픈소스 프로젝트에서 가장 중요한 License는 내가 만들 때에도, 배포할 때에도 가장 신경써
야 하는 일 중 하나입니다.
가장 많이 사용하는 License는 다음과 같습니다.
- MIT License
   - MIT에서 만든 라이센스로, 모든 행동에 제약이 없으며, 저작권자는 소프트웨어와
관련한 책임에서 자유롭습니다.
- Apache License 2.0
  - Apache 재단이 만든 라이센스로, 특허권 관련 내용이 포함되어 있습니다.
- GNU General Public License v3.0
  - 가장 많이 알려져있으며, 의무사항(해당 라이센스가 적용된 소스코드 사용시 GPL을 따라야 함)이 존재합니다.
## git bash 명령어
1. 파일 이름 수정
    - git에서는 파일이름을 수정하면 기존거는 삭제되고 바뀐이름의 파일이 추가된걸로 인식됨
    - git을 붙이면 변경된 이름으로 추적함
```bash
$ mv hello.py helloworld.py -> worst
$ git mv hello.py helloworld.py -> good
```


2. 커밋을 잘못하였을때 최신의(HEAD) 커밋단계로 파일을 되돌림
```bash
$ git restore [file name]
```
3. git add 후 다시 되돌릴 때
```bash
$ git reset HEAD [file name]
```
4. git commit 메시지 작성 되돌리기
```bash
$ git commit --ammend
```
5. commit 다중 파일 되돌리기  
  HEAD: 최신, ~3: 3개의 파일을, ..: 순차적으로
```bash
$ git revert -no-commit HEAD~3..
```

## 새로운 Branch 만들기

Branch 만들기
```bash
$ git branch [new branch]
```
Branch 바꾸기
```bash
$ git switch [new branch]
```
Branch 병합
- 새 브랜치를 디폴트브랜치로 땡겨온다는 개념
```bash
$ git merge [new branch]
```

Branch 삭제
- 브랜치 라이프사이클이 끝나면 바로 삭제 해주는게 좋다
```bash
$ git branch -D [branch name]
```
Branch 병합시 문제<br>
브랜치 양쪽에서 같은 파일을 수정 할시 에러 발생
- 파일을 잘 수정해야함

## git-flow

```bash
$ git flow init
```
- Fatal: Working tree contains unstaged changes Aborting 이 발생했을 경우 -> git flow는 변경된 파일이 없는 상태에서 초기화 해주어야 하므로 git stash(변경된 기능 임시 저장) 후에 git flow init 명령어 다시 입력.

새로운 브랜치
```bash
$ git flow feature start [new branch]
```

release 시작
```bash
$ git flow release start [base v]
```

release finish
```bash
$ git flow release finish
```

git push
```bash
$ git push -u origin [new branch]
```

tag push
```bash
$ git push --tags
```

## TEAM-PROJECT

- team 단위 git-flow 전략
### 팀장 flow
1. 팀장이 git repository를 생성 후 디렉토리에 git clone 해온다
```bash
$ git clone [git주소]
```
2. flow init 하면 develop branch가 생성 됨  
    - 파일 생성 (ex:main.js)
```bash
$ git flow init
```

```bash
$ touch main.js
```
3. git add 후 commit 해준다
```bash
$ git add main.js
$ git commit
```
4. develop에서 처음 push 함으로 -u upstream
    - https://pers0n4.io/github-remote-repository-and-upstream/  
upstream & downstream 이해하기

```bash
$ git push -u origin develop
```

5. 팀원에게 깃 주소 전달

---

### 팀원 flow
1. Issues 작성
    - 팀장 레포에서만 이슈가 있음
    - 다른 사람과 작업이 겹치지 않기 위해 작성
2. Fork 를 함
    - 자신의 권한이 된 레포가 본인 깃에 생성됨
3. 자신의 깃에 있는 레포를 clone 해온다
```bash
$ git clone [fork해온 git 주소]
```
4. git flow init
    - develop 브랜치 생성됨
    - 팀장이 생성한 파일 (main.js)도 같이 생성 된다
```bash
$ git flow init
```
5. 기능 개발할때는 feature start
```bash
$ git flow feature start [new branch name]
```
6. file(main.js)에서 작업 후 add, commit
```bash
$ git add main.js
$ git commit
```
7. 개발 종료후 feature finish
  - develop 브랜치로 작업내역이 들어간다
```bash
$ git flow feature finish [new branch name]
```
8. push
```
$ git push -u origin develop
```
9. github 으로 이동
    1. compare & pull request 버튼 활성화 눌러줌  
    1. branch 확인 중요

---
open된 pull request에서 팀원이 추가 작업 후 push를 하게 되면  
열려 있는 pull request의 하위로 내역이 들어 오게 된다.
(작업내역이 섞여버릴 우려가 있음)

## Git prefix

feat: 기능 개발 관련
fix: 오류 개선 혹은 버그 패치
docs: 문서화 작업
test: test 관련
conf: 환경설정 관련
build: 빌드 관련
ci: Continuous Integration 관련

----

feat: Add server.py
fix: Fix Typo server.py
docs: Add README.md, LICENSE
conf: Create .env, .gitignore, dockerfile
BREAKING CHANGE: Drop Support /api/v1
refactor: Refactor user classes
