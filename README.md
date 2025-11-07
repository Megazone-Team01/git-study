## Git의 작동 원리 ###
- Repository 내에서 모든 작업이 이루어짐 
### Branch: 레포지토리 내에 존재하는 분기점 ####
  - Remote Branch( 원격 브랜치 ) : Git 서버에 업로드 되어 있는 원격 저장소 명칭
  - Local Branch( 로컬 브랜치 ) : 현재 작업하는 장치에 존재하는 로컬 저장소 명칭
  > 원격 브랜치와 로컬 브랜치랑 이름이 같다고 항상 똑같은 상태로 존재하는 것은 아님
### Git 작업을 하면서 신경써줘야 하는 것 ###
1. 현재 작업하는 코드가 최신 코드인지 확인
   - fetch를 통해 최신화
2. 현재 로컬에서 작업 중인 브랜치가 자신이 작업하는 브랜치인지 확인
   - git pull 작업을 진행하면 원격의 모든 브랜치가 로컬로 clone됨
   - 이 때, 기본적으로 default 브랜치가 주 브랜치로 설정
3. push 작업 전 코드 내에 Secret 정보가 없는지
   - Git에 Key값 같은 것이 노출되면 경고 알림이 옴..
   - 이를 위해 '환경 변수'가 사용됨
4. 작업 후 commit은 일반적으로 아래 순서로 이루어짐
   - add >> status >> commit >> push 
### Commit = 코드 파일 업로드
- 작업 이후 코드를 업로드하는 작업을 의미 ( 정확한 의미 '작업 내용' )
- 통상적으로 작업하고 push하는 것까지는 1커밋이라고 칭함
### Git에 작업 내용을 Commit하는 과정 ###
> git add . 
- 작업한 파일들을 이번 Commit에 포함하는 작업
> git status
- 이번 작업에 포함되는 파일 목록 확인
> git commit -m "{커밋 메시지}"
- commit 단위 생성 및 메세지 작성
> git push origin {원격 브랜치 이름}
- 이번 commit을 {원격 브랜치 이름}으로 push ( 업로드 )
- 신규 브랜치를 만들고 첫 push일 경우 원격 저장소에는 해당 브랜치가 없기 때문에 아래 명령어로 생성과 동시에 push하는 작업을 진행
  - **git push -u origin {신규 원격 브랜치 이름}**

## 자주 사용하는 Git 명령어 ###

### git remote add origin {Repository 주소} ####
- git remote add origin https://github.com/Megazone-Team01/git-study.git
    > https://github.com/Megazone-Team01/git-study.git 주소의 레포지토리를 origin이라는 이름의 원격 주소로 등록한다. 
### git fetch origin ###
    > 현재 브랜치를 연결된 원격 브랜치와 동기화
### git checkout {로컬 브랜치명} ###
- git checkout feature-login
    > 작업하는 로컬 브랜치를 {로컬 브랜치명}으로 이동
### git checkout -b {신규 로컬 브랜치명} ###
- git checkout -b feature-logout
    > 새로운 로컬 브랜치를 만들고 해당 로컬 브랜치로 이동
### git merge {대상 브랜치명}
- git merge develop
    > 현재 작업 중인 브랜치에 대상 브랜치 정보를 가져와 병합한다.
    > 현재 작업 중인 브랜치를 베이스로 대상 브랜치의 정보를 덮어쓰며 병합하는 작업
    > 원격 브랜치의 정보를 현재 로컬 브랜치에 병합하고자 할 때는 아래와 같이 표기
        - git merge origin/{원격 브랜치명}
