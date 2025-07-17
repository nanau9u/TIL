# Git

## 분산 버전 관리 시스템

- Git은 분산 버전 관리 시스템이다.

### 중앙 집중식과 분산식

- 중앙 집중식: 버전은 중앙 서버에 저장되고, 중앙 서버에서 파일을 가져와 다시 중앙에 업로드

  - 위키피디아 생각하면 편하다. 위키피디아는 모든 문서를 들고 있고, 내가 수정을 원하는 페이지 하나만 가져와 수정한 뒤 다시 위키피디아에  건네주는 방식

- 분산식: 내게 위키의 복사본이 있고, 복사본을 수정한 다음, 그 수정한 내역들을 중앙에 보내주면 중앙에서 수정하는 방식

  - 모든 개발자들이 각각 위키 사본을 가지는 느낌.
  - **분산 구조에서의 장점**
    - 중앙 서버에 의존하지 않고도 동시에 다양한 작업을 수행할 수 있다.
      - 개발자들 간의 작업 충돌을 줄여주고 개발 생산성을 향상시켜준다.
    - 중앙 서버의 장애나 손실에 대비하여 백업과 복구가 용이하다.
    - 인터넷에 연결되지 않은 환경에서도 작업을 계속할 수 있다.
      - 변경 이력과 코드를 로컬 저장소에 기록하고, 나중에 중앙 서버와 동기화한다.

### 분산 버전 관리 시스템, git

    - 코드의 ‘변경 이력(버전, 히스토리)’을 기록하고 이전 버전과의 변경 사항을 비교하여, ‘협업’을 원활하게 하는 도구

    - 하나의 폴더가 하나의 프로젝트 느낌

### git의 3가지 영역
- Working Directory, Staging Area, Repository

    Working Directory는 작업 공간같은 느낌 (실제 작업 중인 파일이 위치하는 영역)

    ⇒ Working Directory에서 작업을 할 때, 뭔가 추가하려고 추가하면 Staging Area(중간 준비 영역)로 들어간다

    ⇒ Staging Area의 수정할 내용을 전부 수정해서 저장하려고 저장 버튼을 누르면
    
    ⇒ Repository로 넘어간다. 

### Commit = 버전

- 변경된 파일들을 저장하는 행위. 마지 사진을 찍듯이 기록한다 하여 ‘Snapshot’라고도 한다.


```python
$ git -v
git version 2.47.1.windows.1ㅡ
# git 버전 표시

$ git init
Initialized empty Git repository in C:/Users/SSAFY/Desktop/git-practice/.git/
# 깃 로컬 저장소 설정 (초기화)

$ git add sample.txt
# git에 추가할 준비 (staging area로 이동)

$ git status
# 현재 변경 사항 내역 + staging area 표시

$ git commit -m "first commi(메모)"
Author identity unknown
# staging에 있는 내용을 기록 => 레포지토리(저장소)로 파일이 들어간다.
# 해당 시점의 버전을 생성하고 변경 이력을 남긴다.

$ git config --global user.email "nanau9u@gmail.com"
$ git config --global user.name "Jiyeon Song"
# commit 생성을 위해 작성자 정보 입력 

$ git log
commit 722eb3504f87cf56a4e42343cae1a27de86dd110 (HEAD -> master)
Author: Jiyeon Song <nanau9u@gmail.com>
Date:   Thu Jul 17 11:57:18 2025 +0900

$ rm -rf .git/
# 깃으로 관리 종료 (잘못 init해서 데스크탑을 깃으로 관리하기 시작해 버렸거나, 
# 프로젝트를 종료할 때 사용하는 코드)


$ ls -a
#이 안에 git이 있을 경우 없애줄 것 (이상한 데에 생겼을 확률이 높음)**

```


### git 기타 명령어

```python

git status
# 현재 로컬 저장소의 파일 상태 보기

git log
# commit history 보기

git log --oneline
# commit 목록 한 줄로 보기

git config --global -l
# git global 설정 정보 보기 
# 글로벌은 (정확한 의미는 아니지만) 컴퓨터 전체라는 뜻

```

### git init 주의사항

- git 로컬 저장소 내에 또 다른 git 로컬 저장소를 만들지 않는다
- git 저장소 안에 또 다른 git 저장소가 있을 경우 가장 바깥쪽의 git 저장소가 안쪽의 git 저장소의 변경사항을 추적할 수 없기 때문이다.
- 하나의 프로젝트를 하나의 폴더로 관리!! 파이썬 폴더 안에 Day 1 2 3 4 … 이런식으로 날짜 단위로 관리하지 말고, 깃 했으면 git 폴더 만들고, 또 다른 걸 배웠을 땐 새로운 폴더를 만들어 관리할 것.

### git commit 메시지 수정하기

- git commit —amend   커맨드 입력해서 vim으로 진입

    i = 입력모드

    esc = 입력모드탈출

    :wq = 수정한거 저장하고 끝

- 또 다른 메시지 수정 방법은:

``` python

$ git commit --amend -m "amend commit"

```

### git commit 수정하기

```python

$ git log

$ git add README.md

$ git commit --amend

$ git log
commit 696a81591962b9cb4d85997d0f4629d13ebc7a7e (HEAD -> master)
Author: Jiyeon Song <nanau9u@gmail.com>
Date:   Thu Jul 17 11:57:18 2025 +0900

    first commit

$ git log --oneline
696a815 (HEAD -> master) first commit

```