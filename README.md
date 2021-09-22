# Study_Git
업무에 필요한 Git에 대한 학습 내용입니다.

## 1. 시작하기
### 1-1. 버전 관리
---
버전 관리 시스템(VCS - Version Control System)은 파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템.

#### 로컬 버전 관리
버전을 관리하기 위해 디렉토리로 파일을 복사하는 방법   
작업하던 디렉토리를 지워버리거나, 실수로 파일을 잘못 고칠 수도 있고, 잘못 복사할 수도 있다.

#### 중앙집중식 버전 관리(CVCS)
파일을 관리하는 서버가 별도로 있고 클라이언트가 중앙 서버에서 파일을 받아서 사용(Checkout)한다.   
모두 누가 무엇을 하고 있는지 알 수 있다.   
하지만, 서버가 한 시간 동안 다운되면 그동안 아무도 다른 사람과 협업할 수 없고 사람들이 하는 일을 백업할 방법도 없다.

#### 분산 버전 관리 시스템(DVCS)
저장소를 히스토리와 더불어 전부 복제한다.   
대부분의 DVCS 환경에서는 리모트 저장소가 존재한다. 그래서 사람들은 동시에 다양한 그룹과 다양한 방법으로 협업할 수 있다.

<br>

### 1-2. 짧게 보는 Git의 역사
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EC%A7%A7%EA%B2%8C-%EB%B3%B4%EB%8A%94-Git%EC%9D%98-%EC%97%AD%EC%82%AC)

<br>

### 1-3. Git 기초
---
각 파일의 변화를 시간순으로 관리하면서 파일들의 집합을 관리하는 다른 시스템에 반면,   
Git은 데이터를 파일 시스템 스냅샷의 연속으로 취급하고 크기가 아주 작다.   
또한, 성능을 위해서 파일을 새로 저장하지 않는다. 단지 이전 상태의 파일에 대한 링크만 저장한다.   
마치 데이터를 스냅샷의 스트림처럼 취급한다.

#### 거의 모든 명령을 로컬에서 실행
프로젝트의 모든 히스토리가 로컬 디스크에 있기 때문에 모든 명령이 순식간에 실행된다.   
네트워크에 접속하고 있지 않아도 커밋할 수 있다.

#### Git의 무결성
Git은 데이터를 저장하기 전에 항상 체크섬을 구하고 그 체크섬으로 데이터를 관리한다.

#### Git은 데이터를 추가할 뿐
Git으로 무얼 하든 Git 데이터베이스에 데이터가 추가 된다. 되돌리거나 데이터를 삭제할 방법이 없다.

#### 세 가지 상태
Committed - 데이터가 로컬 데이터베이스에 안전하게 저장됐다는 것을 의미한다.   
Modified - 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않은 것을 말한다.   
Staged - 현재 수정한 파일을 곧 커밋할 것이라고 표시한 상태를 의미한다.

#### Git 프로젝트의 세 가지 단계
Git 디렉토리 - Git이 프로젝트의 메타데이터와 객체 데이터베이스를 저장하는 곳을 말한다.
워킹 트리 - 프로젝트의 특정 버전을 Checkout 한 것이다. 작업 영역.
Staging Area - 단순한 파일이고 곧 커밋할 파일에 대한 정보를 저장한다.

<br>

### 1-4. CLI
---
Git의 모든 기능을 지원하는 것은 CLI 뿐이다.   
CLI를 사용할 줄 알면 GUI도 사용할 수 있지만 반대는 성립하지 않는다.   
그러므로 CLI에 대한 내용을 학습하겠다.

<br>

### 1-5. Git 설치
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98)

<br>

### 1-6. Git 최초 설정
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

<br>

### 1-7. Git 도움말
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EB%8F%84%EC%9B%80%EB%A7%90-%EB%B3%B4%EA%B8%B0)

<br>

## 2. Git의 기초
### 2-1. Git 저장소 만들기(Git Bash 활용)
---
#### 1. 기존 디렉토리를 Git 저장소로 만들기
1. 작업 폴더 생성
2. $ git init(.git 파일 생성)
3. 이후 스테이징 및 커밋 작업

#### 2. 기존 저장소를 Clone 하기
$ git clone "Git 저장소 주소" ("지정할 디렉토리명")

<br>

### 2-2. 수정하고 저장소에 저장하기
---
#### 워킹 디렉토리 속 파일의 종류
1. Tracked -  Unmodified, Modified, Staged
2. Untracked
<br>

#### 파일의 라이프 사이클
![사이클](https://git-scm.com/book/en/v2/images/lifecycle.png)

#### 파일 상태 확인
$ git status

#### 파일 추적하기
$ git add 파일이름   
Untracked -> Tracked(Staged) or Tracked(Modified) -> Tracked(Staged)   
git add 후 파일 수정시 git add 다시 한 후 커밋할 것

#### 파일의 상태 간단하게 확인
$ git status -s or --short

#### 파일 무시하기
.gitignore 파일 생성 후 내용 기입

#### Staged와 Unstaged 상태의 변경 내용을 확인
$ git diff

#### 변경사항 커밋하기
1. $ git commit
2. i 입력 후 커밋 메세지 작성
3. :wq 타이핑 하여 저장 후 vim 종료
4. 커밋 완료 메세지 확인
   
or  

$ git commit -m "Story 182: Fix benchmarks for speed" 와 같이 인라인으로 메세지 첨부 가능

#### 파일 삭제하기
Git에서 파일 제거시   
$ git rm 파일이름 을 통해 Staging Area에서 해당 파일 삭제 후 커밋할 것   
실제 파일도 삭제 된다.

#### 파일 이름 변경하기
$ git mv 원래이름 바꿀이름

<br>

### 2-3. 커밋 히스토리 조회하기
---
$ git log   
-p or --patch : 각 커밋의 diff 결과를 보여줌   
--stat : 각 커밋의 통계 정보   
--pretty : 여러 형식으로 커밋 히스토리 출력

<br>

### 2-4. 되돌리기
---
#### 이전 커밋 수정해서 보내기
$ git commit --amend

#### Staged -> Unstaged
$ git reset HEAD 파일이름

#### Modified -> Unmodified
$ git checkout -- 파일이름

<br>

### 2-5. 리모트 저장소
---
리모트 저장소는 인터넷이나 네트워크 어딘가에 있는 저장소를 말한다.   
리모트 저장소를 관리하면서 데이터를 거기에 Push 하고 Pull 하며 다른 사람들과 함께 일할 수 있다.

#### 리모트 저장소 확인하기
$ git remote (-v)

#### 리모트 저장소 추가하기
$ git remote add 단축이름 URL

#### 리모트 저장소의 데이터 가져오기
$ git fetch 리모트 저장소 이름   
fetch는 데이터를 로컬로 가져오긴 하지만 자동으로 merge하지 않는다(수동으로 merge 필요).   
대신 pull은 자동으로 로컬 브랜치와 merge해준다.

#### 리모트 저장소에 Push 하기
$ git push 리모트 저장소 이름 브랜치 이름   

##### Push가 가능한 경우
1. clone한 리모트 저장소에 쓰기 권한이 있다.
2. Clone 하고 난 이후 아무도 Upstream 저장소에 Push 하지 않은 상태일 때.
3. 2의 반대 경우 다른 사람의 작업을 Merge한 후 Push 가능.

#### 리모트 저장소 살펴보기
$ git remote show 리모트 저장소 이름

#### 리모트 저장소 이름 바꾸기
$ git remote rename 원래이름 바꿀이름

#### 리모트 저장소를 삭제하기
$ git remote remove 리모트 저장소 이름

<br>

### 2.6 태그
---
#### 태그 조회하기
$ git tag

#### 태그 붙이기
##### Lightweight 태그
브랜치와 비슷한데 브랜치처럼 가리키는 지점을 최신 커밋으로 이동시키지 않는다.   
단순히 특정 커밋에 대한 포인터일 뿐이다.   
ex) $ git tag v1.4-lw

##### Annotated 태그
Git 데이터베이스에 태그를 만든 사람의 이름, 이메일과 태그를 만든 날짜, 그리고 태그 메시지도 저장한다.   
ex) $ git tag -a v1.4 -m "my version 1.4"

#### 태그 공유하기
Push는 자동으로 태그를 보내지 않는다.   
$ git push origin 태그

#### 태그를 Checkout 하기
특정 버전의 파일을 Checkout하고 싶을 때   
$ git checkout 태그

<br>

### 2.7 Git Alias
---
$ git config --global alias.별명 명령

<br>

## 3. Git 브랜치
### 3.1 브랜치란 무엇인가
---
개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생긴다.   
코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치다.

#### default 브랜치는 master
Git의 브랜치는 커밋 사이를 가볍게 이동할 수 있는 어떤 포인터 같은 것이다.   
기본적으로 Git은 master 브랜치를 만든다. 처음 커밋하면 이 master 브랜치가 생성된 커밋을 가리킨다.   
이후 커밋을 만들면 master 브랜치는 자동으로 가장 마지막 커밋을 가리킨다.

#### 새 브랜치 생성하기
$ git branch 브랜치   
생성과 동시에 마지막 커밋을 가리키게 된다.   

![사진2](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/2.png)   

#### 브랜치 이동하기
$ git checkout 브랜치   

![사진3](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/3.png)   
HEAD가 이제 testing을 가리킴을 볼 수 있다.   

![사진4](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/4.png)   
한 번 커밋 후 확인시 여전히 HEAD는 testing을 가리키고 있다.

![사진5](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/5.png)   
HEAD를 master로 옮긴 후 커밋하면 다음과 같이 나옴을 볼 수 있다.

<br>

### 3-2. 브랜치와 Merge 의 기초
---
#### 실제 개발을 하며 생길 수 있는 예제
1. 웹사이트가 있고 뭔가 작업을 진행하고 있다.
2. 새로운 이슈를 처리할 새 Branch를 하나 생성한다.
3. 새로 만든 Branch에서 작업을 진행한다.

<br>

이때 급한 문제가 생겨 이 것을 해결하는 Hotfix를 만들어 먼저 merge 해야 한다.   
과정은 다음과 같다.
1. 새로운 이슈를 처리하기 이전의 운영(Production) 브랜치로 이동한다.
2. Hotfix 브랜치를 새로 하나 생성한다.
3. 수정한 Hotfix 테스트를 마치고 운영 브랜치로 Merge 한다.
4. 다시 작업하던 브랜치로 옮겨가서 하던 일 진행한다.

![사진6](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/6.png)   
현재 작업중인 프로젝트   

![사진7](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/7.png)   
이슈 95를 처리하기 위한 새 branch인 iss95를 생성   

![사진8](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/8.png)   
iss95에서 다른 작업 진행   

![사진9](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/9.png)   
급한 문제가 생겨 hotfix를 만들기 위해 master로 이동 후 hotfix 생성하고 새 작업 진행   

![사진10](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/10.png)   
문제 해결시킬 hotfix를 master에 merge한다(master로 이동하여 merge할 것).   
이때 fast-forward방식의 merge를 하게 된다.   

![사진11](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/11.png)   
문제가 해결되었으니 hotfix는 지운 후 iss95로 이동한다.   

![사진12](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/12.png)   
이슈 95를 처리하기 위한 작업이 끝나 iss95를 master에 merge 시킨다(마찬가지로 master로 이동하여 merge할 것).   
이때 3-way방식의 merge를 하게 된다.   

![사진13](https://github.com/HongryeolSeong/Study_Git/blob/main/refimg/13.png)   
hotfix와 마찬가지로 iss95를 삭제함으로써 이슈 처리를 마무리한다.   

<br>

### 3-3. 브랜치 관리
---
#### 브랜치 목록 확인
$ git branch   
-v : 마지막 커밋 확인   
--merged : merge된 브랜치 확인   
--no-merged : merge가 안된 브랜치 확인

<br>

### 3-4. 브랜치 워크플로
---
#### Long-Running 브랜치
1. 안정 버전의 코드를 master에 둔다.
2. 개발이 진행 중 이거나 안정화가 필요한 코드는 다른 브랜치를 만들어 사용한다.
3. 2의 브랜치들을 테스트하여 안정적이라고 판단되면 master에 merge한다.
<br>

중요한 개념은 브랜치를 이용해 여러 단계에 걸쳐서 안정화해 나아가면서 충분히 안정화가 됐을 때 안정 브랜치로 merge 한다는 점이다.

#### 토픽 브랜치
1. master에서 작업을 진행한다.
2. 급하게 생긴 이슈를 처리하기 위해 다른 브랜치를 만들어 작업한다.
3. 필요하다면 상황에 따라 한 이슈를 처리하기 위한 여러 브랜치를 만들어 작업한다.
4. 그 중 괜찮은 방법이 있는 브랜치는 master에 merge하고, 나머지 브랜치는 삭제한다.

<br>

### 3-5. 리모트 브랜치
