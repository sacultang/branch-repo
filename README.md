## README.md 양식
### Project Name
Abstract your project in few lines.
see [project sample page]

### Documentation

### Installation
To install,
```
$ pip install sesame
```
and run 
```
$ python open_sesame.py
```

### Supported Python versions
`>=3.6`

### More Information
```
- [API docs]()
- [Official website]()
```

### Contributing
```
Please see [CONTRIBUTING.md]()
```

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
