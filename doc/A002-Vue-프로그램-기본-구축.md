# Vue 프로그램 기본 구축 따라하기

Vue로 개발하려는 초보자들을 위한 가이드 문서입니다.  
이 장은 Vue 프로그램을 쉽게 초기 구축을 VUE-CLI 3.0을 이용하여 구축 하는 방법을 알려 드립니다. 

> 유영창 : frog@falinux.com

## 페이지 이동

* [전체 목차](../README.md) 
* [이전 단계](./A001-개발-환경-구축.md)
* [다음 단계](./A000-준비중.md)

## Vue 프로그램 기본 구축

개발 환경이 끝났다면 바로 동작하는 vue 프로그램을 만들어 보아야 합니다. 

이 과정 역시 따라하시면 바로 끝납니다. 

### 개발 환경 컨테이너 진입

앞에서 설명한 run-bash.sh 을 실행 하여 개발 환경 컨테니너로 진입합니다. 

~~~ bash
$ cd ~/start-study/docker
$ ./run-bash.sh 
~~~

이 후 설명은 개발 환경 컨테이너로 진입한 후 수행한다는 것을 가정합니다. 

### 새로운 vue 프로젝트 생성

가장 먼저 하는 일은 vue cli 3.0 을 사용하여 새로운 vue 프로젝트를 생성하는 겁니다. 

초보자라면 모르는 내용이 대부분이겠지만 그냥 저를 믿고 따라 오시기 바랍니다. 

보통 최근 트랜드에 맞게 프론트앤드를 Vue로 개발한다면 다음과 같은 내용이 포함됩니다. 

* Babel : 자바스크립트 최신 문법을 사용할 수 있도록 해 줍니다. 
* Router : 웹앱을 작성하기 위해서 필수적인 Vue 패키지 입니다. 
* Vuex : vue 의 데이터를 다루기 위한 필수적인 Vue 패키지 입니다. 
* Linter / Formatter : 자바스크립트의 문법 검사 및 자동 수정 패키지 입니다.
* Unit Testing : Vue 의 단위 테스트를 수행하는 기능입니다. 
* E2E Testing : 사람 대신 프로그램으로 브라우저 동작을 검증하는 기능입니다. 

* apollo : REST API 를 대신하는 최신 서버 API 기능입니다. 
* vuetify : 개발자가 자신없는 예쁜 홈페이지를 만들수 있도록 도와주는 라이브러리입니다.

이 모든 기능을 포함하는 초기 프로그램을 Vue CLI 3.0 으로 쉽게 만들 수 있습니다. 

새로운 프로젝트는 vue create 명령을 사용하여 만들 수 있는데 개발 환경 컨테이너에 진입한 후 다음 명령을 수행합니다.

새로운 프로젝트를 만들때는 다음과 같은 형식의 명령을 수행합니다. 

> vue create 프로젝트이름

프로젝트 이름은 저는 보통 home-main 같은 형식으로 만듭니다. 

home 은 프런트앤드란 의미이고 main 은 "/" 즉 메인 페이지란 의미가 됩니다. 
REST API 라면 api-main 이런 식으로 이름짓습니다. 

보통 프런트앤드 개발시에는 홈페이지와 각 기능을 담당하는 앱으로 나누어 볼수 있는데 
마이크로 서비스 개발을 할 경우에는 링크만 연결될 뿐 서로 다른 역활을 하므로 
분리해 주는 방식으로 개발합니다. 

지금 만드는 것은 그 중 메인 홈페이지를 만들겠다는 의미입니다.
하지만 이 문서에서 진행하는 따라하기는 학습용이므로 분리해서 개발해 가지는 않을 겁니다. 

다음과 같은 명령으로 만듭니다. 

~~~ bash
$ cd /apps
$ vue create home-main
~~~

이렇게 실행하면 다음과 같이 빠른 설치가 가능한 https://registry.npm.taobao.org 저장소를 사용할 것인지를 묻습니다. 당근 빠른게 좋으니 Y 를 입력하고 엔터를 치거나 디폴트 선택인 엔터를 입력합니다.

~~~ plantext
?  Your connection to the default npm registry seems to be slow.
   Use https://registry.npm.taobao.org for faster installation? (Y/n) 
~~~ 

이렇게 실행하면 다음과 같이 Vue CLI는 초기 프로젝트를 디폴트로 만들것 인지, 매뉴얼로 진행할 지를 물어 봅니다.

경험상 매뉴얼로 하는 것이 정신 건강상 이롭습니다. 따라하기는 매뉴얼로 진행합니다. 
화살표 위 아래 키로 이동하여 Manual 을 선택하고 엔터를 치면 ❯ 가 있는 메뉴가 선택됩니다. 

~~~
Vue CLI v3.0.5
? Please pick a preset: 
  default (babel, eslint) 
❯ Manually select features 
~~~

이렇게 매뉴얼로 선택하면 선택 사항이 아래와 같이 나열됩니다.  
위 아래 화살표 키를 이용하여 ❯ 를 원하는 선택 라인으로 이동하고 스페이스를 이용하여 선택을 하거나 해제 합니다.  
선택은 ◉ 로 표시되고 해제는 ◯ 로 표시됩니다.

~~~
Vue CLI v3.3.0
? Please pick a preset: Manually select features
? Check the features needed for your project: 
❯◉ Babel
 ◯ TypeScript
 ◯ Progressive Web App (PWA) Support
 ◉ Router
 ◉ Vuex
 ◯ CSS Pre-processors
 ◉ Linter / Formatter
 ◉ Unit Testing
 ◉ E2E Testing
~~~~

엎애서 설명했듯이 위에 선택된 형태로 만드신 후 엔터를 치면 다음으로 진행합니다. 

앤터를 치면 선택한 항목마다 다음 선택이 필요한 내용을 물어 보면서 진행됩니다. 

~~~
? Use history mode for router? (Requires proper server setup for index fallback in production) (Y/n) 
~~~

위 항목은 Router 선택에 대한 질문인데, 웹페이지 이동시 라우터에 히스토리 기능을 지원할 것인가에 대한 질문입니다. Y 를 선택합니다.

~~~
? Pick a linter / formatter config: 
  ESLint with error prevention only 
  ESLint + Airbnb config 
❯ ESLint + Standard config 
  ESLint + Prettier 
~~~

eslint 문법 검사기를 어떤 것을 사용할 것인가를 묻는데 Standard 를 선택하는 것이 가장 무난합니다. 
다른 것들은 너무 엄격해서 스트레스 만탕을 하루 하루 느끼게 되거나 아예 안하면 나중에 프로그램이 동작 하다가 뒷통수 칩니다. 

~~~
? Pick additional lint features: 
 ◉ Lint on save
❯◉ Lint and fix on commit
~~~

~~~
? Pick a unit testing solution: (Use arrow keys)
❯ Mocha + Chai 
  Jest 
~~~

단위 테스팅 방법을 질문하는데 저는 Mocha 방식을 좋아 합니다. 이후 cypress 도 Mocha 베이스고  
보통 백엔드도 Mocha 방식을 즐겨 하므로 Mocha 선택을 권장 합니다. 
공부 좋아 하시는 분들은 다른 방식을 선택하셔도 괜찮지만 이 따라 하기 부분에서는 다루지 않습니다. 

~~~
? Pick a E2E testing solution: (Use arrow keys)
❯ Cypress (Chrome only) 
  Nightwatch (Selenium-based) 
~~~

E2E 테스팅 방법을 질문하는데 Cypress 를 선택합니다. 
저는 이전에는 Nightwatch 를 사용했었는데 Cypress 가 빠르다는 소식을 듣고 변심 중입니다. 
대신 공부하는 고생길이 다시 시작되었습니다(흑흑)

~~~
? Where do you prefer placing config for Babel, PostCSS, ESLint, etc.? (Use arrow keys)
❯ In dedicated config files 
  In package.json 
~~~

Vue CLI 에 의해서 설치되는 다양한 패키지들은 환경 설정 파일을 가지고 있는 것들이 있습니다. 
이 환경 설정 파일을 어디에 둘 것인가를 질문하는데
각 패키지별 전용 파일로 관리할 것을 지정합니다. 
package.json 을 건드리는 것을 저 개인적으로 싫어하기 때문입니다. 

~~~
? Save this as a preset for future projects? (y/N) N 
~~~

현재까지 설정된 내용을 다른 프로젝트 생성시에 쓰기 위해 저장할 것인가를 묻는데
전 귀찮지만 매번 선택하여 생성합니다. 그래서 아니오를 선택합니다. 

~~~
? Pick the package manager to use when installing dependencies: (Use arrow keys)
❯ Use Yarn 
  Use NPM 
~~~

패키지 인스톨시에 사용할 명령으로 Yarn 을 쓸건지 NPM 을 쓸건지 묻는데 
전 최근에는 Yarn 을 선호합니다. 

이렇게 선택이 끝나면 바로 프로젝트를 생성하고 패키지들을 인스톨 합니다. 

생성과 패키지 설치가 성공적으로 끝나면 다음과 같은 출력을 볼 수 있습니다. 

~~~ plantext
success Saved lockfile.
Done in 8.67s.
⚓  Running completion hooks...

📄  Generating README.md...

🎉  Successfully created project home-main.
👉  Get started with the following commands:

 $ cd home-main
 $ yarn serve

 WARN  Skipped git commit due to missing username and email in git config.
You will need to perform the initial commit yourself.
~~~

마지막에 경고가 있읍니다.
이것은 깃 자동 커밋에 대한 처리가 유저명, 이메일이 설정되어 있지 않아 
"너 스스로 해!" 하는 말이므로 이 문서의 따라하기에서는 무시합니다. 

저는 상위 프로젝트 폴더로 전체 깃 관리를 합니다.
생성된 프로젝트의 git 관련 디렉토리를 제거 합니다. 

~~~
$ cd home-maim
$ rm -rf .git
~~~

이제 초기 home-main 을 구축 했으므로 컨테이너를 나갑니다. 

~~~
$ exit
~~~

### lint 시험 스크립트 - run-lint.sh

Vue cli 로 구축된 후 vue 개발 서버로 개발하면 소스 수정이 실시간으로 웹 페이지에 반영됩니다. 
이때 웹 페이지에도 잘못된 내용이 표시되지만 생각보다 잘 안 보입니다. 
그래서 명령행 문법 검사인 lint 를 실행해서 보는 것이 좋습니다. 

lint 문법 검사를 하는 run-lint.sh 스크립트를 만들어서 사용하는 것이 좋습니다. 

run-lint.sh 이름으로 다음과 같이 작성합니다. 

> [docker/run-lint.sh](https://github.com/kcert2018/start-vue-build-up-guide/blob/master/docker/run-lint.sh)

~~~ bash
#!/bin/bash
echo -e "\\033]2;start home main lint\\007"
docker-compose run --name start-home-main-ds-lint \
  --rm \
  -u $(id -u ${USER}):$(id -g ${USER}) \
  --workdir /apps/home-main/ \
  start-home-main-ds \
  yarn run lint
~~~

앞에서 설명한 run-bash 와 내용은 비슷한데 가장 마지막 줄인 yarn run lint 만 다릅니다. 

이 명령으로 사용 가능한 것은 apps/home-main/package.json 의 scripts 세션에 선언된  키  이름들입니다.

> apps/home-main/package.json
~~~ json
{
  "name": "home-main",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "serve": "vue-cli-service serve",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint",
    "test:e2e": "vue-cli-service test:e2e",
    "test:unit": "vue-cli-service test:unit"
  },
    :
~~~

위 처럼 현재까지 진행으로 생성된 package.json 의 scripts 세션 각 키의 의미는 다음과 같습니다. 

* serve - 개발 서버를 수행하여 실시간 웹 수정이 가능하도록 만듭니다. 
* build - 서비스를 하는 실제 서버에 올릴 배포 패키지를 만듭니다. 
* lint - 문법을 검사하고 수정 위치와 원인을 알려 줍니다. 
* test:e2e - E2E 테스트를 수행합니다.
* test:unit - 단위 테스트를 수행합니다. 

자 이제 만든 run-linut.sh 스크립트를 이용하여 문법 검사를 다음과 같이 수행해 봅니다.
이것은 패키지가 잘 설치되고 새 프로젝트가 잘 생성되었는지 검사 하는 의미도 있습니다.

다음과 같이 실행 결과가 나오면 잘 된 겁니다. 

~~~ bash
$ ./run-lint.sh 

yarn run v1.9.4
$ vue-cli-service lint
 DONE  No lint errors found!
Done in 1.71s.
~~~

### 단위 시험 스크립트 - run-unit.sh

보통 개발 과정에서는 run-lint 로 문법 검사만 수행하다가 실제로 하나의 단위 작업이 끝나면 단위 테스트를 수행해서 문제가 없는지 검사 합니다. 
태스트 주도 개발 인 TDD 나 BDD 방식으로 개발하면 단위 테스트는 해당 페이지를 개발 하기 전에 작성됩니다. 

국내의 대부분 개발 문화는 이 부분을 많이 무시하는데. 그래서 개발 속도가 늦죠(아 안습~~~)

어쨌든 처음 하시는 분은 단위 시험을 생활화 하여 조기 퇴근하는 문화를 만들기 바랍니다. 

그래서 단위 테스트 환경이 잘 구축 되어 있는 확인도 할 겸, run-unit.sh 스크립트를 만들어서 시험해 봅니다. 

run-unit.sh 이름으로 다음과 같이 작성합니다. 

> [docker/run-unit.sh](https://github.com/kcert2018/start-vue-build-up-guide/blob/master/docker/run-unit.sh)

~~~ bash
#!/bin/bash
echo -e "\\033]2;start home main unit\\007"
docker-compose run --name start-home-main-unit \
  --rm \
  -u $(id -u ${USER}):$(id -g ${USER}) \
  --workdir /apps/home-main/ \
  start-home-main-ds \
  yarn run test:unit
~~~

앞에서 설명한 run-lint 와 내용은 비슷한데 가장 마지막 줄인 yarn run test:unit 만 다릅니다. 

다음과 같이 실행 결과가 나오면 잘 된 겁니다. 

~~~ bash
$ ./run-unit.sh 

 WEBPACK  Compiled successfully in 2824ms
 MOCHA  Testing...

  HelloWorld.vue
    ✓ renders props.msg when passed

  1 passing (26ms)

 MOCHA  Tests completed successfully

Done in 4.65s.
~~~

### E2E 시험 스크립트 - run-e2e.sh

각 화면이 하나 끝나거나 전체가 화면 단위로 돌아가면 사용자가 실제로 보거나 동작 시키는 것이 정상적으로 수행되는지 시험을 해야 합니다. 

브라우저 상태로 동작하는 것을 시험하는 이것을 E2E 로 합니다. 

당근 프로그램으로 자동화 하여야 하지 않겠습니까?
언제까지 클릭질을 하시면 디버깅하시겠습니까?

이런 E2E 시험을 하기 위해서, cypress 테스트 환경이 정상적으로 구축되었는지를 확인하기 위해서 run-e2e.sh 스크립트를 만들어서 시험해 봅니다. 

run-e2e.sh 이름으로 다음과 같이 작성합니다. 

> [docker/run-e2e.sh](https://github.com/kcert2018/start-vue-build-up-guide/blob/master/docker/run-e2e.sh)

~~~ bash
#!/bin/bash
echo -e "\\033]2;start home main e2e\\007"
docker-compose run --name start-home-main-e2e \
  --rm \
  -u $(id -u ${USER}):$(id -g ${USER}) \
  --workdir /apps/home-main/ \
  start-home-main-ds \
  yarn run test:e2e --headless
~~~

앞에서 설명한 run-unit 와 내용은 비슷한데 가장 마지막 줄인 test:e2e --headless 만 다릅니다. 

다음과 같은 실행 결과가 나오면 잘 된 겁니다. 

~~~ bash
$ ./run-e2e.sh 

yarn run v1.9.4
$ vue-cli-service test:e2e --headless
 INFO  Starting e2e tests...
 INFO  Starting development server...
 98% after emitting CopyPlugin                                                   

 DONE  Compiled successfully in 2877ms                                                                                                                                                                                                12:13:19

 
  App running at:
  - Local:   http://localhost:8080/ 

  It seems you are running Vue CLI inside a container.
  Access the dev server via http://localhost:<your container's external mapped port>/

  Note that the development build is not optimized.
  To create a production build, run yarn build.

 ✔  Verified Cypress! /apps/.cypress-cache/3.1.4/Cypress

====================================================================================================

  (Run Starting)

  ┌────────────────────────────────────────────────────────────────────────────────────────────────┐
  │ Cypress:    3.1.4                                                                              │
  │ Browser:    Electron 59 (headless)                                                             │
  │ Specs:      1 found (test.js)                                                                  │
  └────────────────────────────────────────────────────────────────────────────────────────────────┘


────────────────────────────────────────────────────────────────────────────────────────────────────
                                                                                                    
  Running: test.js...                                                                      (1 of 1) 
(node:236) Warning: Promise.defer is deprecated and will be removed in a future version. Use new Promise instead.
(node:236) Warning: Promise.defer is deprecated and will be removed in a future version. Use new Promise instead.


  My First Test
    ✓ Visits the app root url (534ms)


  1 passing (579ms)


  (Results)

  ┌─────────────────────────┐
  │ Tests:        1         │
  │ Passing:      1         │
  │ Failing:      0         │
  │ Pending:      0         │
  │ Skipped:      0         │
  │ Screenshots:  0         │
  │ Video:        true      │
  │ Duration:     0 seconds │
  │ Spec Ran:     test.js   │
  └─────────────────────────┘


  (Video)

  - Started processing:   Compressing to 32 CRF
  - Finished processing:  tests/e2e/videos/test.js.mp4 (0 seconds)


====================================================================================================

  (Run Finished)


      Spec                                                Tests  Passing  Failing  Pending  Skipped 
  ┌────────────────────────────────────────────────────────────────────────────────────────────────┐
  │ ✔ test.js                                   566ms        1        1        -        -        - │
  └────────────────────────────────────────────────────────────────────────────────────────────────┘
    All specs passed!                           566ms        1        1        -        -        -  

(node:236) Warning: a promise was created in a handler at /apps/.cypress-cache/3.1.4/Cypress/resources/app/packages/server/lib/cypress.js:21:20 but was not returned from it, see http://goo.gl/rRqMUw
    at Function.Promise.cast (/apps/.cypress-cache/3.1.4/Cypress/resources/app/packages/server/node_modules/bluebird/js/release/promise.js:195:13)
Done in 14.79s.
~~~

### 개발 서버 실행 - run-dev.sh 

새로 작성된 Vue 프로젝트를 실행 볼 대망의 시간이 되었습니다. 

역시 개발 서버 프로그램을 실행하기 위해서 run-dev.sh 이란 스크립트를 만들 것입니다. 

run-dev.sh 이름으로 다음과 같이 작성합니다. 

> [docker/run-dev.sh](https://github.com/kcert2018/start-vue-build-up-guide/blob/master/docker/run-dev.sh)

~~~ bash
#!/bin/bash
echo -e "\\033]2;start home main develop(all) sever\\007"
docker-compose run --name start-home-main-dev \
  --rm \
  -u $(id -u ${USER}):$(id -g ${USER}) \
  --workdir /apps/home-main/ \
  start-home-main-ds \
  yarn run serve

~~~

앞에서 설명한 run-unit 와 내용은 비슷한데 가장 마지막 줄인 serve 만 다릅니다. 

다음과 같이 수행하여 개발 서버를 동작 시킵니다. 

~~~ bash
 $ ./run-dev.sh 

yarn run v1.9.4
$ vue-cli-service serve
 INFO  Starting development server...
 98% after emitting CopyPlugin                                                   

 DONE  Compiled successfully in 1675ms                                                                                                                                                                                                12:23:55

 
  App running at:
  - Local:   http://localhost:8080/ 

  It seems you are running Vue CLI inside a container.
  Access the dev server via http://localhost:<your container's external mapped port>/

  Note that the development build is not optimized.
  To create a production build, run yarn build.
~~~

제대로 동작하는지를 확인 하기 위해서 크롬 브라우저를 실행하고 http://localhost:8080/ 로 접속해 봅니다. 

접속 후 개발 과정에는 습관적으로 F12 키를 눌러 개발 창을 엽니다. 

다음은 정상적으로 동작하는 화면입니다. 

여러분들도 여기까지 보였다면  
오우! 추카 추카...

[**A000: 초기 구축 실행 화면**]
![A000 초기 구축 실행 화면](doc/images/A000-vue-first.png)

## apollo 패키지 추가 

슬프지만 여기가 끝이 아닙니다.  
프런트앤드는 백엔드 없이 동작하지 않습니다. 
예전에는 REST API 라는 방식과 소켓만으로 서버에 접근했지만 이제 막강한 GraphQL 도 지원해야 합니다. 프런트앤드에는 GraphQL 사용하기 위한 막강한 툴인 apollo 가 있습니다.

당연히 Vue CLI 3.0 도 apollo 를 초기 구축에 사용할 수 있습니다. 

apollo 패키지를 추가 하기 위해서 run-bash.sh 을 사용하여 개발 환경 컨테이너로 들어 갑니다.

~~~
$ ./run-bash.sh
~~~
그리고 vue add apollo 명령을 사용하여 apollo 를 추가 합니다. 

~~~
$ cd home-main
$ vue add apollo
~~~

패키지 인스톨이 끝나면 apolo 관련된 선택 사항에 대한 질문이 나옵니다. 

~~~
  ? Add example code (y/N) Y
~~~

에제 코드를 추가 할 것인가를 묻습니다. 
앞으로의 학습을 위해서 Y 를 선택합니다. 

~~~
  ? Add a GraphQL API Server? (y/N) Y
~~~

테스트용 GraphQL API 서버를 추가할 것인가를 묻습니다. 
개발을 편하게 하기 위해서 Y 를 선택합니다. 

~~~
  ? Enable automatic mocking? (y/N) Y 
~~~

자동 목킹을 활성화 할 것인가를 묻습니다. Y 를 선택합니다. 

~~~
  ? Add Apollo Engine? (y/N) N
~~~

아폴로 엔진을 사용할 것인가를 묻습니다. 
이것은 apollo 개발 회사가 제공하는 플랫폼을 사용할 것인가를 묻는데 아니오인 N 를 선택합니다. 

설치 과정이 진행이 끝나면 exit 명령을 수행하여 컨테이너를 종료 합니다. 

~~~
$ exit
~~~

이제 앞에서 작성한 스크립트들을 차례로 수행하여 정상적으로 진행되는 가를 확인 합니다. 

~~~
$ ./run-lint.sh
$ ./run-unit.sh
$ ./run-e2e.sh 
~~~~

이 과정은 앞과 동일하므로 이 문서에는 기술하지 않겠습니다. 

이제 apollo 를 추가 한 것이 제대로 되었는지 확인하기 위해서 run-dev.sh 를 수행할 것입니다. 

개발 서버를 띄우기 전에 apollo API 개발 지원 서버를 먼저 수행해 주어야 합니다. 

run-dev-apollo.sh 스크립트를 다음과 같이 작성하고 실행 합니다. 

> [docker/run-dev-apollo.sh](https://github.com/kcert2018/start-vue-build-up-guide/blob/master/docker/run-dev-apollo.sh)

~~~ bash
#!/bin/bash
echo -e "\\033]2;start home main develop apollo sever\\007"
docker-compose run --name start-home-main-dev-apollo-server \
  --rm \
  -u $(id -u ${USER}):$(id -g ${USER}) \
  --workdir /apps/home-main/ \
  start-home-main-ds \
  yarn run apollo
~~~

앞에서 설명한 run-dev 와 내용은 비슷한데 가장 마지막 줄인 apollo 만 다릅니다. 

다음과 같이 수행하여 개발용 apollo 서버를 동작 시킵니다. 

~~~ bash
$ ./run-dev-apollo.sh

yarn run v1.9.4
$ vue-cli-service apollo:watch
$ vue-cli-service apollo:run --delay
Using default PubSub implementation for subscriptions.
You should provide a different implementation in production (for example with Redis) by exporting it in 'apollo-server/pubsub.js'.
✔️  Automatic mocking is enabled
✔️  GraphQL Server is running on http://localhost:4000/graphql
✔️  Type rs to restart the server
~~~

apollo 개발 서버를 수행한 후 프런트 앤드 개발 서버를 실행합니다. 

~~~ bash
 $ ./run-dev.sh 
~~~

크롬 브라우저를 실행하고 http://localhost:8080/ 로 접속해 봅니다. 

화면상에 특별하게 바뀐것은 없습니다. 왜냐하면 apollo 프런트 앤드 화면은 샘플로만 
제공 되기 때문입니다. 

여기서는 설치만 확인 하는 수준으로 만족합니다. 이 후 따라하기 과정에서 다룰 것입니다. 

## vuetify 패키지 추가 

vuetify 는 구글 매터리얼 디자인을 구현해 놓은 스타일 프레임워크 패키지 입니다. 
유명한 부트스트랩 같은 겁니다. 

이 패키지는 vue 명령으로 설치하지 않고 yarn 으로 설치 합니다. 
그래서 만들어진 소스를 살짝 고쳐야 합니다. 
당장은 화면 변화는 없겠지만 이후 목적하는 프로그램을 만들어 가면서 수정할 것입니다.

apollo 패키지를 추가 했던 과정과 유사 합니다. 

수행 중이던 개발 서버 컨테이너를 중지 하고 run-bash.sh 을 사용하여 개발 환경 컨테이너로 들어 갑니다.

~~~
$ ./run-bash.sh
~~~

그리고 yarn add -D vuetify 명령을 사용하여 vuetify 모듈을 추가 합니다. 

~~~
$ cd home-main
$ yarn add -D vuetify
   :
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
info Direct dependencies
└─ vuetify@1.4.1
info All dependencies
└─ vuetify@1.4.1
Done in 20.60s.
~~~

vuetify 를 이용해 화면을 구성하다보면 매터리얼 디자인 아이콘을 자주 사용하게 되는데
이 와 관련된 패키지를 다음과 같이 추가 합니다. 

~~~
$ yarn add -D material-design-icons-iconfont
   :
[4/4] Building fresh packages...
success Saved lockfile.
warning Your current version of Yarn is out of date. The latest version is "1.13.0", while you're on "1.9.4".
info To upgrade, run the following command:
$ curl --compressed -o- -L https://yarnpkg.com/install.sh | bash
success Saved 1 new dependency.
info Direct dependencies
└─ material-design-icons-iconfont@4.0.3
info All depend
~~~

개발 환경 컨테이너를 exit 명령으로 종료 하고 다음과 같이 소스를 수정합니다. 

main.js 의 import 선언된 끝 부분에 다음을 추가 합니다. 

> apps/home-main/src/main.js

~~~
import Vuetify from 'vuetify'
import 'vuetify/dist/vuetify.min.css'
import 'material-design-icons-iconfont/dist/material-design-icons.css'

Vue.use(Vuetify)
~~~

vuetify 는 폰트로 구글의 Roboto 폰트를 사용합니다.
Roboto 는 구글 사이트에서 제공하고 이 폰트 링크를 포함 시켜야 합니다.
index.html 파일의 <head> 태그 사이에 다음과 같이 추가 해야 합니다.

~~~ html
<link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons' rel="stylesheet">
~~~

> apps/home-main/public/index.html

~~~ HTML
    :
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons' rel="stylesheet">
    <title>home-main</title>
  </head>
   :
~~~

이제 기본적인 추가가 끝났으므로 먼저 다음 스크립트를 실행하여 이상이 없는가를 검증합니다.

~~~
$ ./run-lint.sh
$ ./run-unit.sh
$ ./run-e2e.sh 
~~~~

이제 run-dev.sh 스크립트를 실행하여 프런트 앤드 개발 서버를 실행합니다.

크롬 브라우저를 실행하고 http://localhost:8080/ 로 접속해 봅니다. 

F12 를 눌러 개발자 도구를 활성화 하여 Console 창에 에러가 없는가를 확인 합니다. 

여기까지 아무 문제가 없다면 

진짜 진짜 축하 드립니다. 이제 개발만 하면 됩니다. 

저도 여기까지 쓰느라 죽는 줄 알았습니다. 
만세~~~

