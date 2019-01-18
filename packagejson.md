# package.json

각 필드에 대한 설명

## name
패키지 이름
* 214자를 넘으면 안된다.
* . 이나 _ 로 시작하면 안된다.
* 대문자를 쓰면 안된다.
* URL 안전 문자만 사용해야 한다.
* 하이픈(-)은 가능하다.

## version
Semantic Versioning 에 의거하여 작성

## description
패키지에 대한 설명. 패키지를 검색 할때도 사용한다.

## keywords
패키지를 검색 할 때 유용한 문자열 배열

## license
특정한 이유가 없는 오픈 소스 라이센스를 사용

## homepage
패키지 홈페이지

## bugs
이슈 트래커 URL

## repository
실제 소스 코드가 위치한 URL

## author
패키지 저자

## contributors
패키지 기여한 사람들

## files
프로젝트에 포함된 파일. 단일 파일, 전체 디렉토리, 와일드 카드등 사용 가능

## main
프로젝트의 기본 기능을 담당하는 파일

## bin
실행 파일 설치

## man
매뉴얼 페이지가 있으면 추가

## directories
패키지를 설치할 때 정확한 위치를 지정하여 설치 할 수 있다.

## scripts
빌드 프로세스나 개발 도구를 사용하는 방법을 자동화 할때 사용한다.

## config
스크립트에 사용 된 구성 옵션 또는 매개 변수

## dependencies
의존성

## devDependecies
개발 의존성

... 그외 의존성

## flat
패키지가 특정 의존성의 한 버전만 허용

## resolutions
중첩 된 의존성 버전을 대체 할 수 있다.

## engines
패키지와 함께 사용해야하는 클라이언트 버전을 지정한다.

## os
운영체제 호환성을 지정한다.

## cpu
CPU 아키텍처 호환성을 지정한다.

## private
패키지 관리자에 게시하지 않으려면

## publishConfig
publish 관련 옵션
