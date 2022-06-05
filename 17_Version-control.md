# 버전관리(Version control System)

# 💻 Git 기본 사용법

## git이란?

> git은 버전관리 시스템으로 프로그래밍을 하며 그때그때 수정사항을 기록하고 버전을 저장하기 위해 사용

<br>

## git 작업의 구성요소

* git 작업의 구성요소는 크게 로컬 저장소와 온라인 저장소로 나뉘어진다.
* 온라인 저장소가 origin이 되어 여러 명의 개발자들이 자신들의 로컬 저장소로 branch를 따와서 작업을 하여 자신만의 버전을 만든다.
* 작업을 끝낸 후에 프로젝트의 메인 디렉토리인 master branch에 자신들의 branch를 합친다.

<br>

## $git init

> 빈 git 저장소를 만들거나 기존 저장소를 다시 초기화 하는 명령어

<br>

## git config --global user.email
## git config --global user.name

> github 사이트에서 이용하는 이메일과 이름인 내 정보를 등록하는 명령어

* 로컬 컴퓨터에서 git의 config를 설정함으로써 초기 설정을 수행할 수 있다.
* github의 계정 필요

<br>

## git clone 레포지토리 주소

> 다른 git의 저장소를 복사하는 명령어

<br>

## 로컬 저장소와 원력 저장소 연결

```
>>> git remote add origin 레포지토리 주소
```
* 이 명령은 origin이라는 이름으로 레포지토리 주소에 적은 저장소를 원격 저장소(Remote repository)로 등록하라는 명령
* 앞으로는 긴 URL 대신 origin으로 짧게 사용 가능

<br>

## 원격 저장소에 Push/Pull

* 로컬 저장소는 git이 관리하는 세 그룹으로 나뉘어져 있다.
* 첫 번째 그룹 : Working directory, 실제 파일들로 구성
* 두 번째 그룹 : Index, 준비영역(staging area)의 역할
* 세 번째 그룹 : HEAD, 최종 확정본(commit)을 나타냄

<br>

## $git add

> 버전 관리를 할 파일 등을 추가하는 과정. 

<br>

## $git commit -m '커밋 설명'

> 커밋을 하는 명령어로 커밋할 때 구체적인 설명을 같이 입력  
> 이 과정까지 하면 작업 내용이 HEAD에 반영 됨

## $git push origin master

> origin 서버에 master branch로 `push`하라는 명령

## $git pull origin master

> 원격 저장소에서 로컬 저장소로 불러오는 명령  
> 기본적으로 git을 이용한 작업을 시작할 때 꼭 수행해주고 시작해야함

<br>

## $git log

> 커밋 기록을 보여줌

<br>

## $git checkout 커밋번호 7자리
## git checkout -# 가장 최신으로 돌리기

> checkout 명령어는 버전 관리를 복구할 수 있는 시점을 바꾸는 명령어  
> 커밋 번호가 존재하며 커밋번호 앞 7자리를 이용하여 시점을 이동

<br>

## 추가 용어 정리 

### fork

> 다른 사람의 원격 자장소를 이용하기 위해 내 원격 저장소로 복사하는 것

### pull request

> 협력자가 원본 저장소의 관리자에게 merge를 요정하는 과정으로 협력자가 관리자에게 승인을 허가하도록 요청

