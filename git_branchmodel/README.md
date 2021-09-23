# Git 협업 개발 모델
Git 활용시 타 시스템에 비해 branch와 merge 작업이 간단하고 활발히 이루어진다.   
그러므로 이를 이용하여 버전 관리를 효율적으로 하도록 한다.   
   
![flow](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/main.png)

<br/>

## 1. Main branches
사용자에게 가장 친숙한 master 그리고 이와 병렬을 이루는 develop이 있다.

### master
HEAD의 소스코드가 항상 production-ready 상태인 branch.

### develop
HEAD의 소스코드가 항상 다음 릴리스에 대한 최신 개발 변경 사항이 적용된 상태인 branch.

<br/>

## 2. Supporting branches
main branch들을 돕는 branch들이 있다.   
1. 팀원들의 병렬 개발을 지원한다.
2. 기능을 쉽게 추적한다.
3. 제품 릴리즈를 준비한다.
4. live production 문제 해결 작업을 돕는다.   

main branch들과는 다르게 수명이 있어 작업이 끝나는 경우 삭제한다.   
해당 브랜치들은 다음과 같다.   
- Feature branches
- Release branches
- Hotfix branches

<br/>

### 2-1. Feature branches
---
향후 릴리즈 또는 더 뒤에 올 릴리스의 새 기능을 개발하는데 이용된다.   
   
develop로 부터 분기되어야하고,   
develop에 병합되어야 한다.   
   
![사진1-1](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/1-1.png)   

#### 작업 순서
1. 새 기능 작업 시작시 develop에서 분기후 HEAD를 feature branch로 옮긴다.   
$ git checkout -b feature develop
2. 새 기능 작업을 한다.
3. 기능 작업이 끝나면 다시 develop으로 이동한다.   
$ git checkout develop
4. develop에 feature를 병합한다.   
$ git merge --no-ff feature
5. feature를 삭제한다.   
$ git branch -d feature   
   

참고로 4번에서 병합시 --no-ff를 쓰는 이유는 항상 새로운 커밋 개체를 생성하여   
커밋 히스토리 추적에 용이하고,   
기능을 추가한 커밋과 함께 그룹화하기 위함이다.

#### 결과
![사진1](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/1.png)   

<br/>

### 2-2. Release branches
---
새로운 release를 분기하는 순간은 develop이 새 릴리즈가 준비된 상태의 소스코드일 때 이다.   
이 때 예정 릴리즈를 대상으로하는 기능은 모두 포함(merge)되어야하고,   
다음 릴리즈를 대상으로 하는 기능은 다음 release의 분기를 기다려야 한다.   
   
develop으로 부터 분기되어야하고,   
develop와 master에 병합되어야 한다.   

#### 작업 순서
1. develop에서 새로 분기한다.   
$ git checkout -b release-1.2 develop
2. 작업본이 새 버전을 반영하도록 한다.   
$ ./bump-version.sh 1.2
3. 커밋한다.   
$ git commit -a -m "Bumped version number to 1.2"
4. master로 이동하고 병합한다.   
$ git checkout master   
$ git merge --no-ff release-1.2   
5. 태그를 붙인다.   
$ git tag -a 1.2   
![사진3](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/3.png)   
6. develop으로 이동하고 병합한다.   
$ git checkout develop   
$ git merge --no-ff release-1.2   
![사진4](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/4.png)   
7. release를 삭제한다.   
$ git branch -d release-1.2   
![사진6](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/6.png)   

<br/>

### 2-3. Hotfix branches
---
갑자기 발생한 live production 문제에 즉시 대처하기위한 branch이다.   
핵심은 develop에서 팀원들은 작업을 계속할 수 있고, 다른 사람이 빠른 수정안을 준비하고 있다는 것이다.   
   
matser로 부터 분기되어야하고,   
develop와 master에 병합되어야 한다.   
   
![사진8-1](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/8-1.png)   

#### 작업 순서
1. master에서 새로 분기한다.   
$ git checkout -b hotfix-1.2.1 master
2. 작업본이 새 버전을 반영하도록 한다.   
$ ./bump-version.sh 1.2.1
3. 커밋한다.   
$ git commit -a -m "Bumped version number to 1.2.1"
4. 문제 해결을 위한 작업을 한다.
5. 커밋한다.   
$ git commit -m "Fixed severe production problem"
6. master로 이동하고 병합한다.   
$ git checkout master   
$ git merge --no-ff hotfix-1.2.1   
7. 태그를 붙인다.   
$ git tag -a 1.2.1   
![사진8](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/8.png)   
8. develop으로 이동하고 병합한다.   
$ git checkout develop   
$ git merge --no-ff hotfix-1.2.1   
![사진9](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/9.png)   
9. release를 삭제한다.   
$ git branch -d hotfix-1.2.1   
![사진10](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/10.png)   

<br/>

## 최종 결과
위의 모든 작업을 마치고 리모트 저장소에 push한 상태는 다음과 같다.   
   
![사진12](https://github.com/HongryeolSeong/Study_Git/blob/main/git_branchmodel/refimg/12.png)   
   
   
