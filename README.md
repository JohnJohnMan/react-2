# react 3학년 2학기
# 202030427 전준만

## 1120

### use client 란?

- Next.js 13에서 도입된 새로운 지시어로, 컴포넌트가 클라이언트 사이드에서만 렌더링된다는 것을 명시

-  Server Components와 Client Components가 있는데 이 둘을 구분하기 위함이다.

### use client 주요 특징과 사용 이유

- 동적 데이터와 상호작용 : 실시간 채팅, 동적 폼 검증, 클라이언트 사이드에서만 가능한 계산이나 데이터 처리 등 클라이언트 사이드에서 처리해야 하는 동적인 데이터와 상호작용에 적합

- 브라우저 API 접근 : 클라이언트 사이드 렌더링을 통해 브라우저의 API, 예를 들어 window나 navigator와 같은 글로벌 객체에 접근할 수 있다. 이는 서버 사이드에서는 불가능한 작업

- 성능 최적화 : 필요한 경우에만 클라이언트 사이드 렌더링을 사용함으로써, 서버의 부담을 줄이고 전체 애플리케이션의 성능을 최적화할 수 있다. 특히, 초기 페이지 로드 시 필요하지 않은 리소스의 로딩을 방지할 수 있다.

### 주요 Directory & File

- app : Routing Page 관리
- components : 재사용 가능한 공통 컴포넌트 관리
- features : 재사용이 불가능하거나 많은 수정을 해야 하는 컴포넌트 관리
- context : 기능별 컴포넌트 관리
- store : Redux store 설정 파일 관리
- styles : CSS, Sass 등 스타일 파일 관리

### Redux

** Slice **
- Redux Toolkit에서 사용되는 용어로, 특정 기능과 관련된 상태와 Reducer를 한 곳에서 정의하는 곳
 
** Provider **
- Redux Provider는 Redux의 상태 등을 공급하기 위한 파일입니다.
- Provider를 사용하고자 하는 Page에서 사용하면 됩니다.
- 다만 전역적으로 사용할 때는 layout 파일에 정의하면 를 사용해야 하기 때문에 별도위 컴포넌트를 만들어서 사용하는 것이 좋다.

### Context API 와 Redux 비교

- **Context API**
  - React에서 기본으로 제공하는 상태 관리 도구
  - Context API는 주로 전역 상태를 관리
  - React.createContext()로 생성한 Context 객체와 Provider 
  - 장점
  컴포넌트 트리의 깊이 제한 없음
  외부 라이브러리 설치 필요 X
  - 단점
  복잡한 상태 관리
  성능 문제가 있음
  디버깅 도구 부족
- **Redux**
  - Redux는 전역 상태를 관리하기 위한 독립적인 state 관리 라이브러리
  - 상태의 변경을 예측 가능하게 하고, 전역 state 관리를 더 구조적으로 지원
  - store, reducer, action 등의 개념을 사용해 state와 state dispatch를 관리
  - 
  - 장점
    - 명확한 상태 관리 구조
    - 미들웨어 지원
    - 디버깅 도구
    - 모든 프레임워크와 호환

  - 단점
    - 설정 코드의 복잡도
    - 추가 라이브러리 필요
    - 작은 애플리케이션에는 과한 설정

## 1113

### Props의 흐름
- Next.js의 데이터 흐름은 단방향으로 이루어 짐
- 즉, parents에서 child component의 방향으로 props의 흐름이 이루어짐
- 계층 구조가 복잡해지면 Props Drilling 문제가 발생
- Props Drilling은 여러 개의 component를 지나 props가 전달 되면서 발생하는 문제

문제점
1. 중간 컴포넌트에 불필요한 프로퍼티 전달
2. 프로퍼티 데이터 형식 변경의 불편함
3. 누락된 프로퍼티 인지의 어려움
4. 프로퍼티 이름 변경 추적의 어려움


### Context API
- context는 UX 구축에 많이 사용되는 React의 기능
- React는 16.3 버전부터 정식적으로 context api를 지원
- 일반적으로 props는 부모에서 자식으로 전달되는 단방향 통신을 합니다.
- Context API는 특정 component가 props를 사용하지 않고, 하위 component를 포함한 모든 component에 데이터를 공유할 수 있는 기능을 제공
- 전역으로 데이터를 사용할 수 있도록 해줌

- Context API는 createContext, Provider, useContext 개념만 알면 적용이 가능

## 1106

### UI 라이브러리
- UI 라이브러리, 프레임워크, 유틸리티는 필수 X
- 생산성 향상 및 UI 일관성

- chakra UI
  - 버튼, Modal, 입력 등 다양한 내장 컴포넌트 제공
  - dark mode, light mode 지원
  - 타입스크립트로 작성되어 있음

  ```sh
  npm i @chakra-ui/react @emotion/react
  npx @chakra-ui/cli snippet add
  ```

- TailwindCSS
  - 다른 프레임워크와는 다르게 CSS 규칙만을 제공
  - JS 모듈이나 react 컴포넌트를 제공하지 않기 때문에 필요한 경우 직접 만들어서 사용해야 함
  - 변수값을 조정하여 개성있는 디자인을 만들 수 있음. 디자인 자유도가 높다.
  - dark mode 및 light mode를 쉽게 적용할 수 있다.
  - 빌드 시점에 사용하지 않는 클래스는 제거 되기 때문에 높은 수준의 최적화를 지원
  - CSS 클래스의 접두사를 활용해서 모바일, 데스크톱, 태블릿 화면에서 원하는 규칙을 지정할 수 있음

- Headless UI
  - TailwindCSS를 만든 Tailwind Labs 팀의 무료 오픈소스 프로젝트
  - TailwindCSS는 웹 컴포넌트 안에서 사용할 수 있는 CSS클래스만 제공함
  - Headless UI는 CSS클래스를 제공하는 것이 아닌 동적 컴포넌트만 제공한다.

  ```sh
  npm install @headlessui/react
  ```

## 1030

### CSS와 내장 스타일링 메서드
- Styled JSX
  - Styled JSX는 CSS-in-JS 라이브러리이다.
  - 내장 모듈이기에 설치가 필요 없음

  - 단점
    - IDE나 코드 편집기 등 개발 도구에 대한 지원이 부족
    - 문법 하이라이팅, 자동 완성, 린트(lint)기능을 제공 X
    - 코드 내에서 CSS에 대한 의존성이 점점 커지기 때문에 앱 번들도 커지고 느려짐

- CSS Module
  - CSS-in-JS의 단점을 보완하기 위한 방법이다.
  - .module.css 로 끝나는 파일에서 CSS클래스를 가져와서 사용
  - 변환한 객체에서 모든 키는 클래스 이름을 의미함
  - 클래스들은 컴포넌트 스코프를 가진다.
  - 생성된 HTML 태그를 보면 class 가 고유한 값을 갖는다.
  - CSS Module 상속

- SASS
  - Next에서 기본으로 지원하는 전 처리기
  - 단 패키지 설치가 필요함 ( npm install sass )
  - SASS 및 SCSS(Sassy CSS) 문법으로 CSS Module을 만들고 사용할 수 있다.
  - styles/Home.module.css 파일 이름을 styles/Home.module.scss로 바꿔주면 된다.

## 1023

### 누적 레이아웃 이동 
- 정적 자원 중 이미지 파일은 SEO에 많은 영향을 미친다.
- 다운로드 시간이 많이 걸리고, 렌더링 후에 레이아웃이 변경되는 등 UX에 영향을 미친다.
- Image 컴포넌트를 사용하면 해결
- lazy loading : 이미지 로드 시점을 필요할 때까지 지연시키는 기술
- 이미지 사이즈 최적화로 사이즈를 1/10이하로 줄여줌
- placeholder를 제공

### Image Component

#### local 방식
  - Image 컴포넌트 사용 시 주의 사항
  - width, height는 필수이다. (layout="fill"을 사용 시에는 생략)
  - layout="responsive" 는 브라우저 크기에 맞게 가변한다.

### Remote 방식
- Pixabay와 같은 외부 이미지를 사용하려면 next.config.mjs 설정이 필요

### 코드 구성과 데이터 불러오기
- 프로젝트를 시작할 때 확장과 복잡도에 대비 해야한다.
- 코드를 더 효율적으로 구성하기 위해 아토믹 디자인 원칙에 따라 디렉토리를 구성한다.
  - atoms : 가장 기본적인 컴포넌트 관리
  - molecules : atoms에 속한 컴포넌트 여러 개를 조합하여 복잡한 구조로 만든 컴포넌트 관리
  - organisms : molecules와 atoms를 섞어서 더 복잡하게 만든 컴포넌트 관리
  - templates : 위의 모든 컴포넌트를 어떻게 배치 결정해서 사용자가 접근할 수 있는 페이지

## 1025


## 1002


### 단일 동적 경로
단일 동적 경로는 [] 안에 동적 값을 하나만 받는 라우트
예를 들어, /pages/bar/[foo].jsx는 단일 동적 경로임 여기서 foo는 URL에서 동적으로 변하는 값

```jsx
  // pages/bar/[foo].jsx
  export default function FooPage({ params }) {
    return <h1>{params.foo}</h1>;
  }
```
/bar/123을 방문하면 123이 foo에 전달됨

### 다중 동적 경로

다중 동적 경로는 [...]을 사용해 여러 세그먼트를 배열로 처리하는 라우트

예를 들어, /pages/bar/[...foo].jsx는 다중 동적 경로임 여기서 foo는 배열로 전달되며, 여러 경로를 동적으로 처리할 수 있음

```jsx
  // pages/bar/[...foo].jsx
  export default function FooPage({ params }) {
    return <h1>{params.foo.join('/')}</h1>;
  }

```

/bar/a/b/c로 접속하면 ['a', 'b', 'c']가 foo에 전달됨

### 선택적 동적 경로

선택적 동적 경로는 [[...]]을 사용하여 경로 세그먼트가 없어도 접근 가능한 라우트
예를 들어, /pages/bar/[[...foo]].jsx는 선택적 다중 동적 경로임 foo가 없어도 라우트에 접근할 수 있음

```jsx
  // pages/bar/[[...foo]].jsx
  export default function FooPage({ params }) {
    return <h1>{params.foo ? params.foo.join('/') : 'Home'}</h1>;
  }
```

/bar/로 접속하면 Home이 출력되고, /bar/a/b로 접속하면 a/b가 출력됨

### 동적 라우팅

동적 라우팅은 중첩이 가능
동적 라우팅은 경로의 일부가 변할 수 있도록 설정하는 방식임
예를 들어, URL의 일부를 변수처럼 사용해 다른 데이터를 보여주게 됨
동적 라우팅에서는 [] 또는 [[]]와 같은 구조를 사용

```jsx
    export default function FooId(props) {
    return (
      <>
        <h1>
          Foo {props.params.fooId} {props.searchParams.country}
        </h1>
      </>
    );
  }
```

URL - http://localhost:3001/posts/007?id=jjm&name=jjm
URL - http://localhost:3001/blog01/1004?id=jjm&name=jjm

### 정리

동적 라우팅: 경로의 일부를 동적으로 처리하는 방식

단일 동적 경로: 하나의 세그먼트만 동적으로 처리하는 경로 ([foo].jsx)
다중 동적 경로: 여러 세그먼트를 배열로 처리하는 경로 ([...foo].jsx)
선택적 동적 경로: 세그먼트가 없어도 접근 가능한 다중 동적 경로 ([[...foo]].jsx)

## 0925

### Next.js 기초와 내장 컴포넌트

#### 클라이언트와 서버에서의 라우팅 시스템 작동 방식

 Next는 파일시스템 기반의 페이지 라우팅과 앱 라우팅을 함

페이지 라우팅은 /pages 디렉토리 안의 `index.js`, `index.jsx`, `index.tsx` 파일에서 export한 React 컴포넌트

앱 라우팅은 src/app 디렉토리 안에 `page.js`, `page.jsx`, `page.tsx`의 파일에서 export한 React 컴포넌트

동적 라우팅 규칙을 만들려면 페이지 라우팅은 `slug.js` 파일, 앱 라우팅은 slug 디렉토리가 필요함

`slug.js` 는 매개변수로 사용되며 주소창에서 입력하는 값을 모두 받을 수 있음

동적 라우팅 규칙은 중첩도 가능함

접근 경로를 `~/posts/[data][slug]` 형태로 받을 수 있음

ex) app/foo/[fooId]/page.jsx

  ```jsx
  export default async function fooId(props) {
    console.log(props);

    return (
      <h1>
        foo {props.params.fooId} / {props.searchParams.country}
      </h1>
    );
  }
  ```

- URL : http://localhost:3000/foo/2?country=KOR

#### 페이지 간 이동 최적화

Next.js 가 정적 자원을 제공하는 방법

자동 이미지 최적화와 새로운 Image 컴포넌트를 사용한 이미지 제공 최적화 기법

  컴포넌트에서 HTML 메타 데이터를 처리하는 방법

  app.js와 document.js 파일 내용 및 커스터마이징 방법

## 0911

### Transpile

Babel

  ECMAScript 같은 js 최신 버전이나, TypeScript 이전 버전의 코드로 변환 시키는 Transpile 도구

    AST(Abstract Syntax Tree)

    소스 코드를 추상화된 트리 구조로 나타낸 것

    Babel의 parser는 js 코드를 컴퓨터가 이해하기 쉽게 변환해줌

    싱글 쓰레드로 실행되기 때문에 속도가 느리다는 단점

  SWC

  Next 12 이후 Babel에서 SWC로 교체됨

    SWC는 Rust로 작성되어 속도가 훨씬 빠름

  > 속도가 빠른 이유는 Rust에는 WASM(WebAssembly)이라는게 있는데 이게 어셈블리어로 되어있음(저급언어)

### 렌더링 전략

#### 서버 사이드 렌더링(SSR)

  APM을 사용하는 웹 페이지 생성

  자바스크립트 코드 적재되면 동적으로 페이지 내용을 렌더링함

  Next.js도 동적으로 페이지를 렌더링할 수 있음

  리액트 하이드레이션 :

  서버에서 렌더링된 HTML 마크업에 기반하여 클라이언트 측에서 자바스크립트 이벤트와 상태를 연결하는 과정을 말함

  장점
  
  - 안전한 웹 애플리케이션 : 인증 또는 민감한 작업을 서버에서 수행하고 그 결과만 브라우저에 제공해 위협을 피할 수 있음
  - 뛰어난 웹 사이트 호환성 : 클라이언트 환경이 오래된 브라우저도 서비스를 제공함
  - 뛰어난 SEO : 서버가 렌더링한 HTML을 받기에 웹 크롤러가 페이지를 렌더링할 필요가 없음

  단점

  - 페이지간의 이동은 CSR에 비해 느림
  - 서버 과부하
  - 깜빡임 이슈 (매번 새로고침 해야하기 때문에)
- SSR은 만능이 아니다.
  - 단순히 서버가 SPA(Single Page App)를 렌더링한다고 모든 것이 해결되지 않음
  - 오히려 자바스크립트 코드를 증가시키며, 애플리케이션이 인터렉티브 할 때까지 걸리는 시간이 단순 클라이언트 렌더링보다 더 길어질 수 있음

#### 클라이언트 사이드 렌더링(CSR)
- 실제 렌더링이 클라이언트에서 이루어지는 방식
- React 앱을 실행하면 렌더링 시작 전에 빈 화면이 한동안 유지 되는 것이 보임

  **장점**
  - 네이티브 앱처럼 느껴지는 웹 앱

    - 전체 자바스크립트 번들을 다운로드 한다는 것은 렌더링할 모든 페이지가 이미 브라우저에 다운로드 되어 있다는 뜻

    - 다른 페이지로 이동해도 서버에 요청할 필요 없이 바로 이동

    - 페이지를 바꾸기 위해 새로 고침이 없음

  - 쉬운 페이지 전환

    - 클라이언트에서 네비게이션이 새로고침이 발생하지 않아 UX에 도움이 됨

  - 지연된 로딩과 성능

    - 초기 로딩 이후 빠른 웹사이트 렌더링이 가능(웹사이트가 로딩되는 즉시 상호작용 가능)

  **단점**
  - 네크워크가 속도가 느린 환경에서는 번들이 모두 다운로드 될 때까지 빈 페이지를 보아야함

  - 검색 로봇에게도 그 내용은 빈 것으로 보임

  - 번들을 모두 받을 때까지 검색 로봇이 기다리기는 하지만 성능 점수는 낮음

#### 정적 사이트 생성(SSG)
SSG는 일부 또는 전체 페이지를 빌드 시점에 미리 렌더링

**장점**
1. 쉬운 확장 : 정적 페이지는 HTML 파일으므로 CDN을 통해 파일을 제공하거나, 캐시에 저장하기 쉬움

2. 뛰어난 성능 : 빌드 시점에 미리 렌더링하기 때문에 페이지를 요청해도 클라이언트나 서버가 무언가를 처리할 필요가 없음

3. 더안전한 API 요청 : 외부 API를 호출하거나, DB에 접근하거나, 보호해야 할 데이터에 접근할 일이 없음
   필요한 모든 정보가 빌드 시 포함되어 있기 때문임

## 0904

### Chocolatey

  Chocolatey (약칭 Choco) : 윈도우에서 사용할 수 있는 커맨드 라인 패키지 매니저

  > Linux 커맨드라인 패키지 매니저 : apt(apt-get), yum  
  > Mac 커맨드라인 패키지 매니저 : Homebrew

  설치 / 업데이트 / 삭제 등 에 사용하는 Windows용 패키지 매니저

  설치 URL : https://chocolatey.org/install

  패키지 URL : https://community.chocolatey.org/packages

  명령어

  ```shell
  # 패키지 목록
  choco search
  choco list

  # 패키지 원격 검색
  choco list 패키지명

  # 패키지 모든 버전 원격 검색
  choco list -a 패키지명
  choco install 패키지이름

  # 무조건 수락
  choco install -y

  # 특정 버전 선택 설치
  choco install 패키지명 --version 버전

  # 윈도우 11환경에서 안 될 시
  choco install nvm(window 11은 power shell 관리자 모드에서 하면 깔림)

  # 패키지 삭제하기
  choco uninstall 패키지명

  # 패키지 업그레이드
  choco upgrade 패키지명
  ```

  최신 버전 설치

  ```shell
  nvm install node
  nvm install lts # lts 최신버전
  ```

  버전 지정 설치

  ```shell
  nvm install 16.15.1
  nvm install 16 # 16.x 의 마지막 버전

  nvm uninstall <version> # 필요없는 node 버전 삭제하기
  ```

  node 전환

  ```shell
  nvm use <version>

  nvm current # 현재 사용중인 버전 확인하기
  ```

### nvm

NVM (Node Version Manager)는 개발 환경에 따라 Node.js의 버전을 변경해야 하는 상황에 대처하기 위해 필요한 모듈임
  일반 소프트웨어 설치하듯이 exe 파일을 받아 일일히 클릭하여 업데이트 하는 것이 아닌, 터미널에서 명령어로 매우 간단하게 노드 버전을 변경할 수 있음
  nvm-windows는 MIT 라이센스의 오픈 소스로 Go로 작성되었음
  Node.js v4+에서 지원되기 때문에 기본적인 Node.js는 설치가 되어 있어야 함

- 명령어

  ```shell
  # nvm 버전 확인
  nvm -v

  # 현재 내 노드 버전 확인
  nvm ls

  # 사용가능한 노드 버전 확인
  nvm ls available
  ```

### 프로젝트 기본 구조

- Page Router

    기존 13 이전 버전에서의 Next.js는 원래 /pages 폴더 아래에 원하는 페이지 폴더 목록을 만들어 라우팅을 관리하였음
    pages 폴더 안에 `index.js` 가 기본 페이지가 됨
    EX) localhost:3000/about <= pages 폴더 안에 about.js 파일이 있으면 자동으로 라우팅 됨

- App Router

  App Router는 /app 폴더를 이용하여 라우팅을 설정할 수 있다. 즉, app 폴더가 pages 폴더를 대체한다고 봐도 됨
  app 폴더 안에 `page.js` 가 기본 페이지가 됨
  EX) localhost:3000/about <= app 폴더 안에 about폴더 안에 `page.js` 파일이 있으면 자동으로 라우팅 됨

### Next 프로젝트 생성

- 프로젝트 생성

```shell
npx create-next-app@latest
```

- 문제 있을 때(생성이 안 됐을 시)

```shell
npm cache clean --force
npm i -g creata-next-app
```

- 위에 다 해도 안될 때

```shell
node 버전 변경
nvm install 버전
nvm use 버전
```

### 보일러 플레이트
url : https://github.com/vercel/next.js/tree/canary/examples
위 링크에서 필요한 보일러 플레이트를 가지고 와서 사용하면 시간을 줄일 수 있음

## 0828

#### Page Router vs. App Router

React로 개발하다 처음 Next를 사용하면 Router를 볼 수 있음
`Next.js`는 App Router가 Stable하게 지원하기 시작
강의는 App Router로 진행

[Page Router]
page 디렉토리가 root이고, index.js가 index page가 됨
about.js는 /about, team.js는 /team 경로로 `클라이언트 중심의 라우팅` 됨

[App Router]
App 디렉토리가 root이고 page.js가 index page가 됨
/about/page.js는 /about, /login/page.js는 /page 경로로 `서버 중심의 라우팅` 됨
번들 사이즈가 작음

#### Next.js 13 vs 14

Page Router -> App Router
Data Fetching: 13까지는 getServerProps, getStaticProps 메소드를 이용해 구현했으나, 14부터 `SSG`(정적 사이트 생성), `SSR`(서버측 랜더링) 및 `ISR`(증분적 정적 재생성)에서 하나의 API만을 사용해 구현할 수 있게 됨

```jsx
 This request should be cached until manually invalidate.
 Similar to `getStaticProps`
 `force-cache` is the default and can be omitted.
fatch(URL, {cache:`force-cache`});

 This request should be refetched on every request.
 Similar to `getServerSideProps`
fetch(URL, {cache:`no-store`});

 This request should be cached with
```
Tubopack: Rust 기반으로 개발된 새로운 번들러 사용으로 webpack보다 700배 빠르다고 발표

Turbopack 은 3,000개의 모듈이 있는 애플리케이션에서 1.8초만에 부팅되고, Webpack은 16.5초, Vite는 11.4초가 걸림

이미지 최적화: 13까지는 `도구`를 사용했으나, 14부터는 `자체적`으로 지원하기 시작

보안 강화: XXS 공격에 대한 보호 기능이 강화되고, 보안 관련 헤더 설정을 더욱 쉽게 만듬

### Chapter 1. Next.js 알아보기

`Next.js` 는 리액트를 위해 만든 오픈소스 자바스크립트 웹 프레임워크
리액트에 없는 다양한 기능 제공
  * 서버 사이드 랜더링(SSR: Server Side Rendering)
  * 정적 사이트 생성(SSG: Static Site Generation)
  * 증분 정적 재생성(ISR: Incremental Static Regeneration)

```jsx
SSG(정적 페이지 생성)는 미리 만들어 놓은 페이지를 서비스 하기 때문에
속도는 빠르나 한번 생성시 수정 불가능
이러한 단점 보완을 위해 나온 것이 ISR(증분 정적 재생성)
이미 생성된 페이지를 일정 시간이 지난 후에 다시 생성(최신 데이터로 업데이트)
```

[ Chapter 1 주요 내용]
Next.js 소개 / 프레임워크 비교 / 리액트와 차이점
기본 구조 타입스크립트 사용법
바벨과 웹팩 설정 커스터마이징(Next.js14는 Webpack->Tubopack 바뀜)

#### 1.1 준비

Node.js와 npm을 설치하거나, codesandbox.io 혹은 repl.it 등의 사이트 이용
이후 프로젝트별로 필요한 의존성 패키지 npm으로 설치  
`가볍게 이용할 경우 사이트도 좋지만 그렇지 않으면 local에서 환경 설정하는 것이 좋음`

#### 1.2 Next.js란?

Angular, React, Vue 와 같은 프레임워크가 등장하면서 웹 개발 분야 급속도로 변화

1. 리액트는 메타(페이스북)의 `조던 발케`가 제작, 2013년 오픈소스 발표

2. 리액트는 클라이언트 사이드(CSR)에서만 작동하는 문제점이 있음
   * 검색 엔진 최적화(SEO)의 효과를 거의 볼 수 없음
   * 애플리케이션 실행 초기 성능 부담
   * 현재 리액트에서도 SSR을 지원하지만 구현은 `Next.js`보다 복잡
3. 이 문제 해결을 위해 서버에서 미리 렌더링 해두는 방법 연구
4. 이 연구 결과가 `Next.js` (Vercel에서 제공)
5. 이 밖에 리액트가 제공하지 않는 여러 기능을 제공함

[ `Next.js`가 제공하는 새로운 기능들 ]
코드 분할(Splitting): 페이지를 로딩 할 때 번들을 여러 조각으로 나눠 필요한 부분만 전송
파일 기반 라우팅(React 에서는 React-Router-Dom 사용)
경로 기반 프리페칭(Prefetching): 사용자가 다음에 이동할 수 있는 페이지를 미리 가져오는 기술
서버 사이드 렌더링(SSR: 페이지 요청이 올 때마다 사전 렌더링)  
  (페이지 요청 시 Fetching 요소 적용해 렌더링)
정적 사이트 생성(SSG): 빌드하는 동안 페이지 사전 생성  
  (Fetching 요소 적용 위해 재빌드)
증분 정적 콘텐츠 생성(ISR): 배포 후에도 재배포 없이 계속 업데이트(일정 시간마다 SSG 재렌더링)
타입스크립트 기본 지원
자동 폴리필(Polyfill) 적용: 이전 브라우저에서 최신 기능을 제공하는 데 필요한 코드 제공
이미지 최적화: Next/image 컴포넌트로 제공하는 이미지 최적화 기술  
  ( lazy loading-지연, 이미지 사이즈 최적화-webp 변환, placeholder-영역 확보)
웹 애플리케이션의 국제화 지원: 다국어 지원(local에 맞는 URL로 라우팅)
`Next.js`는 현재 넷플릭스, 트위치, 틱톡, 나이키, 우버, 엘라스틱 등 여러 사이트에서 사용중

#### 1.3 Next.js 와 비슷한 프레임워크

[ Gatsby ]
정적 웹 사이트를 만들 수 있는 프레임워크
정적 사이트 생성, 클라이언트 사이드 렌더링만 지원
동적 웹사이트 제작 불가능

[ Razzle ] <https://github.com/jaredpalmer/razzle> / <https://razzlejs.org/>
서버 사이드 렌더링이 가능한 자바스크립트 애플리케이션 개발 가능
CRA와 유사하게 프로젝트를 구성할 수 있는 장점(create-razzle-app)
React, Preact, Reacon-React, Angular 및 Vue 와 함께 사용 가능

[ Nuxt.js ]
Vue를 사용한 웹 애플리케이션 개발에서 리액트의 `Next.js`에 해당하는 프레임워크
Nuxt.js 나 `Next.js` 모두 같은 목표를 갖는 프레임워크지만 Nust.js 는 더 많은 설정 필요
만약 Vue 개발자가 서버 사이드 렌더링이 필요하다면 Nuxt.js 추천

[ Angular Universal ]
정적 사이트 생성과 서버 사이드 렌더링 지원
Nuxt나 Next와는 달리 `구글`에서 만듬
Angular 로 개발하는 경우 대부분 Angular Univeral 사용

2016년 첫 발표

#### 1.4 왜 Next.js 일까

React에서 제공하지 않는 여러 기능 지원
설정이나 개발 옵션 등 다양한 부분에서도 유용한 기능 제공
활동적인 커뮤니티가 있어 개발 단계별로 많은 지원을 받을 수 있음  
  <https://react.dev/learn/start-a-new-react-project>

#### 1.5 리액트에서 Next.js 로

`Next.js`의 기본 철학은 React와 유사
`"설정보다는 관습"` 리액트 철학 계승

"CoC: Convention over Configuration"은 개발자가 해야 할 결정의 수를 줄여주면서도, 유연성은 잃지 않도록 하는 소프트웨어 설계 패러다임

예로 설정 파일을 만들지 않고도 어떤 페이지에서 서버 사이드 렌더링을 적용하고, 어떤 페이지에 정적 페이지 생성을 적용할지 지정 가능
`Next.js` 는 fetch, window, document 와 같은 웹 브라우저에서 제공하는 전역 체계나 canvas 같은 `HTML 요소 접근 불가`
전역 객체나 HTML 요소를 반드시 사용해야 하는 컴포넌트를 다루는 방법 별도 제공

그밖에
클라이언트 사이드 앱, 프로그레시브 웹앱, 오프라인 웹앱도 쉽게 만들 수 있음
많은 내장 컴포넌트와 최적화 기능 사용이 가능하다는 장점  
Progressive Web Apps(PWA)은 웹앱과 네이티브 앱의 장점 모두 제공  
Java, Kotiln / Object-C, Swift

#### 1.6 Next.js 시작하기

개발환경 Node.js 와 npm 설치 (Node.js 설치시 npm 함께 설치됨)
버전 확인 (v22.7.0 버전 사용, 다른 버전도 ok, 의존성 문제시 변경)

```jsx
node -v
npm -v
```
