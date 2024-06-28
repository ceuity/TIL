## GIT Introduction

### Install GIT

- 각 OS에 맞는 패키지 매니저를 이용하여 git을 설치할 수 있다.

### Git Introduction

- `git init` : 현재 디렉토리를 git repo로 초기화
- `git add` : Working Area에 있는 파일을 Staging Area에 추가한다.
    - Staging Area에 추가되면 commit을 하지 않아도 일단 복사하여 저장해두기 때문에 Staging Area에 있는 파일 명으로 새로운 파일을 만들면 해당 파일은 Working Area의 modified 상태로 존재하게 되며, Working Area에 있는 파일을 restore하면 Staging Area의 상태로 restore한다.
- `git commit` : 현재 추가된 파일을 commit
    - commit은 이전 버전으로 돌아갈 수 있는 하나의 checkpoint이다. 따라서 commit을 할 때에는 가장 작은 기능의 단위로 commit하는 것이 좋다. 또한 여러 개의 파일을 동시에 commit하기 보다는 같은 기능 단위의 파일로 commit 하는 것이 좋다.
- `git restore` : modified 상태일 때 수정 사항을 이전 commit으로 되돌리기
- `git log` : commit log를 보여준다.
    - `git log --oneline` : commit log를 한 줄로 요약해서 보여준다.
    - `git log --name-only` : commit 된 파일명을 포함하여 보여준다.
    - `git log --decorate` : branch 명을 보여준다.
    - `git log --graph --decorate` : branch를 graph 구조로 보여준다.

### Git Branches

- `git branch` : branch list를 확인한다.
    - `git branch [branch_name]` : 새로운 branch를 생성한다.
    - `git branch -d [branch_name]` : branch를 삭제한다.
- `git checkout [branch_name]` : 이미 생성된 해당 branch로 스위칭한다.
    - `git checkout -b [branch_name]` : 새로운 branch를 생성과 동시에 스위칭한다.
- HEAD는 현재 branch를 나타내는 pointer이다.

### Initialize Remote Repositories

- `git remote add origin https://.../.../[name].git` : 해당 저장소를 원격 저장소로 추가한다.
    - `git remote -v` : 현재 작동중인 원격 저장소 확인
- `git push origin(remote) master(branch)` : 원격 저장소를 로컬 저장소와 동기화
- `git clone git_repo` : 저장소의 내용을 clone
- `git fetch origin master` : master branch의 내용을 origin으로 fetch
    - 원격 저장소에서 가져온 branch는 `remotes/origin/master` 와 같이 앞에 remotes가 붙는다.
- `git merge origin/master` : origin/master branch를 로컬 저장소랑 merge
- `git pull` : `git fetch` + `git merge`

### Merge Conflict

여러 명이 동시에 merge를 진행할 경우, Git은 누구의 코드를 merge해야 하는지 알 수 없으므로 에디터를 이용하여 수정한 후 다시 merge를 진행한다. 수정한 후에는 `git add` 를 이용하여 다시 추가해준 후, `git merge` 명령어로 merge한다.

### Rebasing

- `git rebase` : commit을 수정한다.
- `git rebase -i HEAD~3` : 텍스트 에디터를 이용하여 interactive rebase를 한다.
- `git cherry-pick <commit_hash>` : 다른 branch의 해당 commit만 master branch에 commit한다.

### Resetting and Reverting

- `git revert <commit_hash>` : 해당 commit의 수정 내용을 반대로 적용한 후 commit에 추가한다.
- `git reset` : commit을 되돌린다.
    - `git reset --soft HEAD~1` : commit 만 되돌린다. (Staging 상태)
    - `git reset --hard HEAD~1` : commit 뿐만 아니라 변경 사항도 되돌린다.

### Stash

- `git stash` : 현재 파일의 변경 사항을 임시 Stage로 이동
- `git stash pop` : 임시 Stage에서 변경 사항을 꺼내오기
- `git stash list` : Stash에 저장되어있는 목록 출력
- `git stash show <stash_number>` : 해당 stash의 변경사항 출력

### Reflog

- `git reflog` : 모든 log를 보여준다. hard reset을 한 경우에도 hard reset 시점의 log가 남아있으므로 해당 pointer로 reset하면 hard reset 하기 전의 상태로 되돌릴 수 있다.
