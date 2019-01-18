# CLI
CLI 명령 정리

기본 5가지 명령

* yarn add
* yarn init
* yarn install (=yarn)
* yarn publish
* yarn remove

## 들어가기 전
`yarn global add <package...>`

전역 의존성을 추가 할 수 있지만 그러지 않는 것이 좋다. 각 프로젝트 별로 명시적으로 패키지를 지정하고 의존성 세트를 지니게 하는 것이 좋다.

## 명령들

### yarn add <package...>
공백으로 하나 이상의 패키지를 설치 할 수 있다.

### yarn add <package...> [--dev/-D]
devDependencies로 패키지를 설치한다.

### [-peer/-P], [--optional/-O]

### [--exact/-E]
정확하게 일치하는 버전만 설치하게 한다.

### [--tilde/-T]
동일한 주요 버전의 최신 릴리즈를 추가하게 한다.

### --audit
알려진 보안 문제를 확인한다.

이 외 add flag 더 있지만 사용 빈도가 높지 않음.

### yarn autoclean [-I/--init] [-F/--force]

autoclean은 의존성에서 불필요한 파일 및 폴더를 제거한다. 이 명령은 고급 사용 사례이므로 별다른 문제가 없다면 사용하지 않는 것이 좋다.

autoclean은 기본적으로 비활성화 되어 있다. 이를 가능하게 하려면 .yarnclean 파일을 수동으로 작성하거나 --init 으로 생성한다. .yarnclean이 패키지에 존재한다면 다음과 같은 경우에 autoclean이 활성화 된다.

* yarn install 후
* yarn add 후
* yarn autoclean --force 실행 하는 경우


### yarn cache list [--pattern]
yarn은 모든 패키지를 파일 시스템의 사용자 디렉토리에 있는 전역 캐시에 저장한다. 위 명령어로 캐시를 확인 할 수 있다.

### yarn cache dir
캐시 경로를 확인한다.

### yarn cache clean [<module_name>]
전역 캐시가 지워진다.

## yarn check
package.json의 패키지 버전과 yarn.lock파일의 버전이 일치 하는지 확인한다.

## yarn help
도움말

## yarn import
npm 프로젝트를 yarn 프로젝트로의 마이그레이션을 도와주며 기존 의존성 트리간의 차이를 최소화한다.

## yarn list
패키지 의존성을 트리 형태로 보여준다.
