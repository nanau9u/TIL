# Remote Repository = 원격 저장소

- 코드와 버전 관리 이력을 온라인 상의 특정 위치에 저장하여 
    여러 개발자가 협업하고 코드를 공유할 수 있는 저장 공간

    대표적으로 GitHub, GitLab, Bitbucket 등이 있음 (서비스라고 생각하면 편함)

```python
$ git remote add origin https://github.com/nanau9u/git-practice.git
# origin이라는 이름의 원격 저장소(remote)를 이 경로에 추가(add)할 겁니다

$ git remote -v
origin  https://github.com/nanau9u/git-practice.git (fetch)
origin  https://github.com/nanau9u/git-practice.git (push)
# 잘 추가됐는지 확인
```

- 별칭을 사용해 로컬 저장소 한 개에 여러 원격 저장소(origin)를 추가할 수 있다.

## push / pull & clone
### push

- 내가 수정한 파일을 원격 저장소에 넣고 싶다!!

```python
git push <name> <branch>
git push origin master
내 저장소의 변경 내역(commit)들을 원격에 푸시한다.
```

### pull & clone

- pull = 원격 저장소의 변경사항만을 받아옴 (업데이트)

- clone =  복제. 새 개발자가 프로젝트에 참여해오고 싶을 때, 깃헙에 올린 프로젝트를 클론(복제)해서 가져오는 것

```python
git clone <url>
# 저장소를 복제해 온다

git pull <name> <branch>
git pull origin master
# 원격 저장소에 있는 내용을 가져온다
```

## gitignore

- = Git이 이 파일들은 무시해줬으면 좋겠어!!

    = Git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는 데 사용되는 텍스트 파일 (대표적으로 API 키 같은 것)

1. .gitignore 파일 생성 (파일명 앞에 '.'입력, 확장자 없음)
2. .gitignore에 무시해주길 원하는 파일 이름 작성
3. git init
4. git status

    - 도움되는 사이트: https://www.toptal.com/developers/gitignore/

        ⇒ gitignore 목록 생성 서비스 : 운영체제, 프레임워크, 프로그래밍 언어 등 개발 환경에 따라 gitignore 목록을 만들어주는 사이트

### comflict

(개발자 A, B 의 커밋이 충돌하는 상황에서의 해소법.)


# GitHub 활용

## TIL

- Today I learned
- 매일 내가 배운 것을 마크다운으로 정리해서 문서화하는 것
    - 단순히 필기만이 아닌, 스스로 더 나아가 어떤 학습을 했는지를 기록하는 것

# 참고
- README.md 파일이란?
  - 프로젝트에 대한 설명, 사용 방법, 문서화된 정보 등을 포함하는 역할
  - Markdown 형식으로 작성되며, 프로젝트의 사용자, 개발자, 혹은 기여자들에게 프로젝트에 대한 전반적인 이해와 활용 방법을 제공하는데 사용
  - 주로 프로젝트의 소개, 설치 및 설정 방법, 사용 예시, 라이선스 정보, 기여 방법 등을 포함
  - 반드시 저장소 최상단에 위치해야 원격 저장소에서 올바르게 출력됨

# Revert & Reset

- 권장하지 않음
- 개발자들끼리 협업할 때 굉장히 위험한 행위이니 쉽게 하지는 말 것. 보통 새로운 커밋을 만드는 게 방법.

## Git revert

- 특정 commit을 없었던 일로 만드는 작업

```python
git revert <commit id>
```

- “재설정”
- 단일 commit을 실행 취소 하는 것
- 프로젝트 기록에서 원하는 commit을 없었던 일로 처리한 후, 그 결과를 새로운 commit으로 추가함

```python
$ git log --oneline
d7c8501 (HEAD -> master) third
91cbd74 second
f7b3a3d first

$ git revert 91cbd74
[master 06421df] Revert "second"
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 2.txt

$ git log --oneline
06421df (HEAD -> master) Revert "second"
d7c8501 third
91cbd74 second
f7b3a3d first
```

- commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit을 생성
    - git 에서 기록이 손실되는 것을 방지함 기록의 무결성과 협업의 신뢰성을 높임

### revert 추가 명령어

```python
git revert 7f6c24c 006dc87 3551584
#  공백을 사용해 여러 commit을 한꺼번에 실행 취소 가능

git revert 3551584..7f6c24c
# `..`을 사용해 범위를 지정하ㅕ 여러 commit 을 한꺼번에 실행 취소 가능

git revert --no-edit 7f6c24c
# commit 메시지 작성을 위한 편집기를 열지 않음 (자동으로  commit 진행)

git reavert --no commit 7f6c24c
# 자동으로 commit  하지 않고, Staging Area 에만 올림 (이후에 직접 commit 해야 함)
# 이 옵션은 여러 commit을 revert할 때 하나의 commit으로 묶는 것이 가
```

## Git reset

- 특정 commit으로 되돌아가는 작업
- “되돌리기”, “역행”, “돌려”
- 시계를 마치 과거로 돌리는 듯한 행위
- 특정 commit으로 되돌아갔을 때, 되돌아간 commit 이후의 commit은 모두 삭제
- push 해버렸으면 reset이 보통 안됨(github에서 거절함), 된다고 해도 굉장히 어렵고 위험한 행위

```python
git reset [옵션] <commit id>
```

### reset의 3가지 옵션

- 삭제되는 commit에 남은 내용을 남길 것인지, 지울 것인지 선택 가능
- —soft, —mixed, —hard
- reset은 과거 commit으로 되돌아간 후 되돌아간 commit이후 commit들이 삭제됨
- 그런데 삭제되는 commit들의 기록을 어떤 영역에 남겨둘 것인지 옵션을 활용해 조정할 수 있음
- —soft
    - 이력만 지우고, 파일은 남겨둔다 (staging area에)
- —hard
    - 이력도 지우고, 파일도 지운다: 상태 자체가 과거로 돌아가는 느낌
    - reset 옵션 중에서도 가장 파괴적
- —mixed
    - 이력은 지우고, 파일은 남아있지만 add되지 않은 상태로 남는다
    - 기본 옵션 값


- 하지만 별로 권장하지 않음!!!!
- reset도 reflog도!!

### git restore

- Modified 상태의 파일 되돌리기
- 뭔가 코드를 막 적어 넣었는데, 적고 보니까 필요없는 것 같음. 마침 add하기도 전이고 원복시키고 싶다. ⇒ restore하면 된다!

### git rm —cached

- Staging area에 올라간 파일을 Unstage 하기
- git rm —cached
- git restore —staged