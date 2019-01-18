# yarn
yarn은 facebook에서 기존 npm의 문제를 극복하기 위해 개발한 Javascript node package manager 이다.

## work flow
프로젝트에 패키지 관리자를 도입하면 종속성에 대한 새로운 워크 플로우가 도입된다. yarn은 워크 플로우의 각 단계를 이해하기 쉽게 만든다.

기본 워크 플로우에 대해 알아야 할 사항
1. 새 프로젝트 만들기
2. 의존성 추가 / 업데이트 / 제거
3. 의존성 설치 / 재설치
4. 버전 관리 작업
5. 지속적인 통합

## 새 프로젝트 만들기
yarn을 추가하려는 디렉토리의 터미널 / 콘솔에서 (거의 항상 프로젝트의 루트) 다음 명령을 실행한다.

`yarn init`

그러면 다음과 같은 대화 형 양식이 열린다.

    name (your-project): 영문소문자만 적는다.
    version (1.0.0): 유의적 버전에 의거하여 적는다.
    description: 간단한 설명을 적는다.
    entry point (index.js): 엔트리 포인트를 적는다. 보통 기본값인 index.js를 많이 사용한다.
    git repostiory: git 레포지토리 주소를 적는다.
    author: 관리자 혹은 작성자를 적는다.
    lincense (MIT): 라이선스를 적는다.

  괄호안의 값은 기본 값이며 직접 입력하거나 enter / return 키를 눌러 기본값을 사용하거나 공백으로 둘 수 있다.

  ## package.json

  yarn init은 package.json 파일을 생성한다. package.json은 프로젝트에 대한 정보를 저장하는데 사용한다. 아래와 같은 내용이 포함되지만 가장 중요한 것은 프로젝트에 어떤 의존성이 설치되어 있는지가 가장 중요하다.

      {
        "name": "my-new-project",
        "version": "1.0.0",
        "description": "My New Project description.",
        "main": "index.js",
        "repository": {
          "url": "https://example.com/your-username/my-new-project",
          "type": "git"
          },
          "author": "Your Name <you@example.com>",
          "license": "MIT"
      }

  ## 의존성 관리
  의존성을 추가, 업그레이드 또는 제거하려면 몇 가지 명령을 알아야 한다.

  각 명령은 자동으로 프로젝트의 package.json 및 yarn.ock 파일을 업데이트 한다.

  ### 의존성 추가
  다른 패키지를 사용하려면 먼저 패키지를 의존 항목으로 추가해야 한다. 그렇기 위해서 다음을 실행한다.

  `yarn add [package]`

  이렇게 하면 자동으로 [package]에 대한 의존성을 package.json에 추가한다. 또한 변경 사항을 반영하여 yarn.lock에 업데이트 된다.

      {
        "name": "my-package",
        "dependencies": {
          "package-1": "^1.0.0"
        }
      }

  플래그를 사용하여 다른 유형의 의존성을 추가 할 수도 있다.

  * yarn add --dev (devDependencies)
  * yarn add --perr (peerDependencies)
  * yarn add --optional (optionalDependencies)

  또응 의존성 버전이나 태그를 지정하여 설치할 패키지 버전을 지정할 수 있다.

`yarn add [package]@[version]` <br />
`yarn add [package]@[tag]`

예)

`yarn add package-1@1.2.3` <br />
`yarn add package-2@^1.0.0` <br />
`yarn add package-3@beta` <br />

### 의존성 업그레이드

    yarn upgrade [package]
    yarn upgrade [package]@[version]
    yarn upgrade [package]@[tag]

### 의존성 제거

`yarn remove [package]`

### 의존성 유형
의존성은 총 5가지의 유형을 갖는다.

#### dependencies
일반적인 의존성. 코드를 실행할 때 필요한 것이다. (React, ImmatubleJs등)

#### devDependencies
개발 의존성. 개발 워크 플로우의 시점에서는 필요하지만 코드가 실행할때는 필요없는 종속성.(Bable, Flow 등)

#### peerDependencies
피어 의존성은 자신의 패키지를 게시하는 경우에만 나타나는 특수한 의존성 유형이다.

피어 의존성이 있으면 패키지를 설치하는 사람과 정확하게 의존하는 의존성이 있어야 한다.

#### optionalDependencies
선택적 의존성은 말 그대로 옵셔널 하다. 설치에 실패해도 yarn은 설치 프로세스가 성공적이라고 말한다.

이는 모든 컴퓨터 혹은 OS에서 반드시 작동하지 않는 의존성 설치에 유용하며 설치 되지 않아도 대비책이 있는 경우이다. (Watchman 등...)

#### bundledDependencies
패키지를 게시(배포)할 때 번들로 제공 될 패키지 이름의 배열이다.

번들 의존성은 프로젝트 내에 있어야 한다. 이 기능은 기본적으로 정상적인 의존성과 같다. 일반적인 의존성은 대개 npm 레지스트리에서 설치된다. 번들 의존성은 일반적인 의존성이 충분하지 않은 경우에 유용하다.

* npm 레지스트리에 제공되지 않았거나 수정 된 타사 라이브러리를 다시 사용하고자 할 때
* 자신의 프로젝트를 모듈로 재사용하고자 할 때
* 모듈과 함께 일부 파일을 배포하려고 할 때

## 의존성 설치
git과 같은 버전 관리 시스템에서 패키지나 프로젝트를 체크아웃 한 경우 해당 프로젝트의 의존성을 설치해야 한다.

### 설치 방법

`yarn install`

프로젝트의 모든 의존성을 설치하는 데 사용된다. 의존성은 package.json 파일에서 검색되어 yarn.lock에 저장된다. 설치 옵션에 따라 설치하게 되면 로컬 `node_modules`폴더에 설치된다.

### 설치 옵션

1. 모두 설치(일반적) `yarn 또는 yarn install`
2. 하나의 패키지 버전만 설치 `yarn install --flat` (의존성 버전의 범위가 넓다면 하나의 버전만 선택하라는 메세지가 나온다.)
3. 모든 패키지를 강제로 다시 다운로드 `yarn install --force`
4. 프로덕션 의존성만 설치 `yarn install --production`

### 기타 옵션
`yarn install --check-files`

이미 설치 했지만 node_modules에서 제거되지 않았는지 확인한다.

`yarn install --har`

설치 중에 모든 네트워크 요청에서 HTTP arqhive를 출력한다.

`yarn install --ignore-scripts`

package.json에 정의된 어떤 스크립트 혹은 의존성 스크립트를 실행하지 않는다.

`yarn install --modules-folder <path>`

패키지가 설치될 경로를 변경

`yarn install --no-lockfile`

yarn.lock 파일을 읽지 않는다.

`yarn install --production`

devDependencies 패키지를 설치하지 않는다. --prod 와 동일

`yarn install --pure-lockfile`

yarn.lock 파일을 생성하지 않는다.

`yarn install --focus`

`yarn install --frozen-lockfile`

yarn.lock을 생성하지않고 업데이트가 필요한 경우

`yarn install --silent`

로그를 생성하지 않는다.

`yarn install ignore-engines`

엔진 검사 무시

`yarn install --igonore-optional`

optionalDependencies를 설치 하지 않는다.

`yarn install --offline`

오프라인 모드로 실행

`yarn install --non-interactive`

대화식 프롬포트를 사용하지 않는다. 부적합한 의존성 버전을 설치할때 처럼

`yarn install --update-checksums`

yarn.lock 파일의 체크섬을 업데히트 하고 패키지의 체크섬이 일치하지 않으면 업데이트 한다.

`yarn install --audit`

설치된 패키지의 알려진 보안 문제를 확인한다. npm과 달리 yarn은 요청 시에만 보안 문제를 검사한다.

`yarn install --no-bin-links`

패키지가 포함 할 수 있는 바이너리에 대한 실행을 금지한다.

## yarn.lock
여러 PC에 일관되게 설치하려면 yarn은 사용자가 구성한 package.json의 정보보다 많은 정보가 필요하다. yarn은 설치된 각 의존성 버전을 정확하게 저장해야 한다.

이를 위해 yarn은 프로젝트 루트에 yarn.lock을 사용한다.

yarn.lock은 yarn에 의해 관리되므로 직접 편집하지 않는다.

## yarn의 버전 관리
yarn의 패키지는 "semver"라고도 하는 시맨틱 버전 관리를 따른다. (자세한 내용은 Semantic Versioning 문서를 확인한다.)

### 버전의 범위를 지정 하는 법

* <2.0.0 : 2.0.0 보다 작은 버전
* <=3.1.4 : 3.1.4 보다 작거나 같은 버전
* \>, >=
* = : 동일한 버전

연산자가 지정되지 않으면 기본적으로 = 연산자가 적용된다.

연산자를 동시에 쓰는 것도 가능하다.

0.4 - 2 처럼 하이픈 범위도 가능 (0.4보다 크거나 같거나 2보다 작거나 같다) 생략된 버전의 범위는 0으로 채워진다.

* \* : 모든 버전
* 2.x : 2.0.0 버전보다 크거나 같거나 3.0.0 미만
* 3.1.x : 3.1.0 버전보다 크거나 같거나 3.2.0 미만

이외 ~로 버전을 지정하는 방법이다 ^로 지정하는 방법이 있다.

## 태그
배포 태그(또는 dist-tags)는 패키지의 게시된 버전을 레이블로 표시하는 방법이다. 버전 번호를 직접 입력하는 대신 레이블을 사용하여 설치할 수 있다.

`yarn add [package]@[tag]`

태그의 종류

1. latest : 최신 패키지 버전
2. stable : 패키지의 최신 안정 릴리즈. 일반적으로 LTS가 없으면 latest와 동일하다.
3. beta : 최신 및 안정화 되기 전의 릴리즈. 완료되기전에 예정된 변경 사항을 공유하는데 사용한다.
4. canary : 프로젝트가 자주 업데이트 되고 많은 사람들이 프로젝트를 사용하면 해당 레이블을 사용하여 이전 코드를 공유 할 수 있다.
5. dev : 버전을 테스트 할 때
