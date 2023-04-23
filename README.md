# Git 매뉴얼

## `.gitignore`

버전 관리 하지 않을 폴더나 파일 이름을 적습니다:

- 빌드 파일
- 비밀 번호
- 환경 변수

## git 그래프 보는 법

- git 그래프에서 가장 중요한 것은 commit hash 입니다.
- 각 브랜치는 commit hash를 바라보고 있습니다.
- 그리고 원격 브랜치(`origin/<SDT-25>`)와 로컬 브랜치(`SDT-25`)를 구분해서 볼 줄 알아야 합니다.

Q. 브랜치가 무엇인가요?

> 커밋을 가리키는 포인터를 브랜치라고 합니다.
>
> 포인터: 커밋 해시를 참조(reference)하는 역할

```sh
* 0af75680d (HEAD -> SDT-4_refactor_remove_stop_propagation) refactor: 모달에 있는 stopPropagation 제거 (3일 전) Min
* a9848a7f6 refactor: main 회원가입 AdditionalInformation 리팩터 (3일 전) Min
* 97779d6f5 refactor: Enter 이벤트 및 스크롤 이벤트 stopPropagation 제거 (3일 전) Min
* 4029f689b refactor: 이직기 복사 버튼에 있는 event.stopPropagation 코드 제거 (3일 전) Min
* 28cce6d91 (origin/main, main) chore: 배포를 위한 버전 변경 (4일 전) Meo
```

## 새로운 개발 작업 시작하기

```sh
# 원격저장소 연결 확인
git remote -v

git remote add origin <주소>
```


```sh
# 01 현재 작업용 브랜치를 생성한다:
git switch -c SDT-25_fix_bug
```

```sh
# 02 ..작업을 한다..

# 작업이 끝나면 git에 어떤 변경이 생겼는지 확인한다
git status

# 작업이 끝나면 현재 커밋과 변경된 사항의 diff를 확인한다
git diff
git diff --staged

# {{{ 취소 }}}
git restore <file>
git restore --staged <file>
```

```sh
# 03 작업이 변경된 내용을 현재 폴더(`.`) 기준으로 모두 add 한다
git add .

# 04 커밋을 한다 (-v: verbose)
git commit -v

# {{{ 취소 }}}
# 상황 A. 내가 커밋하기 바로 직전 최신 커밋으로 돌아가고 싶다
git reset --hard HEAD~
git reset --hard <hash>
```

브랜치 되돌리기:

```sh
# 현재 브랜치가 가리키고 있던 모든 히스토리를 본다
$ git reflog
38922f4 (origin/main, origin/HEAD, main) HEAD@{1}: reset: moving to 38922f43
dc805d6 (HEAD -> SDT-25_fix_bug) HEAD@{2}: commit: fix: 잘못된 앱 이름 수정

# dc805d6로 돌아가기
$ git reset --hard dc805d6
```

```sh
# [누나 컴퓨터] ---SSH(Secure SHell)--- [GitHub 컴퓨터]
# keypair
# ssh key private key                 public key

```
