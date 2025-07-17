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