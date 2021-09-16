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

### 1-2. 짧게 보는 Git의 역사
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EC%A7%A7%EA%B2%8C-%EB%B3%B4%EB%8A%94-Git%EC%9D%98-%EC%97%AD%EC%82%AC)

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

### 1-4. CLI
---
Git의 모든 기능을 지원하는 것은 CLI 뿐이다.   
CLI를 사용할 줄 알면 GUI도 사용할 수 있지만 반대는 성립하지 않는다.   
그러므로 CLI에 대한 내용을 학습하겠다.

### 1-5. Git 설치
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98)

### 1-6. Git 최초 설정
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

### 1-7. Git 도움말
---
[본문 링크](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EB%8F%84%EC%9B%80%EB%A7%90-%EB%B3%B4%EA%B8%B0)
