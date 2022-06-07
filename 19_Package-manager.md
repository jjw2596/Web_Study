# 💻 패키지 매니저

* 소프트웨어를 만들 때 모듈을 이용하는데, 사용하는 모듈이 많아지면 복잡한 문제 발생
* 패키지 매니저는 이러한 모듈들을 관리하는 도구
* 자바스크립에는 npm, yarn, brew가 대표적

# 💻 npm

## 📖 npm이란?

* npm은 node package manager의 약자
* 자바스크립트 패키지 매니저이고 NodeJS에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할을 하며 설치/관리를 수행할 수 있는 CLI를 제공
> CLI : Command Line Interface의 약자, 명령줄 인터페이스

## 📖 의존성 관리

* npm에서는 package.json 파일로 프로젝트의 정보와 패키지들의 의존성을 관리
* package.json에는 사용하고 있는 패키지들의 명세가 작성되어 있기 때문에 프로젝트를 다른 사람에게 공유하고 싶다면 package.json을 공유하여 개발 환경을 빠르게 구축할 수 있다.
* 프로젝트 루트에서 `npm init -y`로 package.json 생성 가능
* package.json에서 name과 version은 생략할 수 없는 기본값

<br><br>

# 💻 yarn

## 📖 yarn이란?

* yarn은 npm의 동작방식과 비슷하고, 페이스북에서 npm의 단점을 보완하여 성능과 속도를 개선한 라이브러리 관리 도구

## 📖 npm과 yarn의 차이점

1. Parallel installation og packages, packages 병렬 설치  
    * 패키지가 설치되면 일련의 작업을 수행한다.
    * npm에서 여러 패키지를 설치할 때, 패키지가 완전히 설치 될 때까지 기다린 후 다른 패키지를 설치 => 작업은 패키지별로 <b>순차적</b>으로 실행
    * yarn은 이러한 작업을 <b>병렬</b>로 설치하므로 퍼포먼스와 속도가 증가

2. Automatic lock file generation, 자동 lock 파일 생성
    * npm과 yarn 모두 패키지에서 프로젝트의 종속성과 버전 번호를 추적
    * json 파일 종속성을 설치할 때마다 종속성 버전이 버전 번호 앞에 ^로 시작 될 수 있다.
    * 즉, 다른 시스템에 모든 패키지를 설치하거나 설치할 명을 수동으로 실행할 때마다 패키지 관리자가 릴리스 된 최신 버전을 찾는다. 
    * 패키지를 자동으로 변경하지 않으려면 두 가지 방법이 있다.
    * 하나는 잠금 파일 생성, 다른 하나는 패키지 파일에 ^을 제거하는 것
    * 종속성이 추가되면 yarn은 yarn.lock 파일을 자동으로 추가
    * npm은 `npm shrinkwarp` 명령어로 lock 파일을 생성
    * npm은 기본적으로 lock 파일을 생성하지 않으나 <b>yarn은 항상 yarn.lock 파일을 생성하고 업데이트</b> 함

3. Security, 보안
    * npm은 다른 패키지를 즉시 포함시킬 수 있는 코드를 자동으로 실행 => 보안 시스템에 여러가지 취약이 발생
    * yarn은 yarn.lock 또는 package.json 파일에 파일만 설치 => yarn이 npm 패키지보다 보안이 강화된 것으로 간주