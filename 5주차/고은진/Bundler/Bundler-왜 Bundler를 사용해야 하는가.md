# 왜 Bundler를 사용해야 하는가?

## Bundler 탄생 배경

인터넷이 등장하고 처음에는 웹 페이지와 서비스들의 규모가 크지 않았지만 점점 대규모 웹 서비스들이 생겨나고 웹 개발에 여러 모듈들을 사용하면서 여러 문제들이 발생했다.

이를 해결하기 위해 탄생한 것이 바로 **Bundler**다.

> 즉 프론트엔드 코드의 근본적인 종속성(dependencies) 문제를 핸들링하기 위함이다.

## Bundler 기능

Bundler는 의존성이 있는 모듈 코드를 하나 혹은 여러 개의 파일로 만들어주는 도구다.

> 모듈: 프로그램 내부를 기능별 단위로 분할한 부분

즉 단순히 자바스크립트 파일들 뿐만 아니라 애플리케이션에 필요한 모든 종류의 파일들을 모듈 단위로 나누어 최소한의 **파일 묶음(번들)**으로 만드는 것이다.

![Image](https://github.com/user-attachments/assets/a001f761-ba83-499f-910d-893b493d71a8)

![Image](https://github.com/user-attachments/assets/4ad7b366-3994-4353-a578-78adec1e99e1)

이외에도 다음과 같은 기능들을 제공한다.

- **코드 축소**
  여러 개의 파일들을 묶을 때 애플리케이션 실행에 사용하지 않은 파일은 포함하지 않는다. 그에 따라 파일의 크기를 줄여 페이지 로딩을 빠르게 하는 효과를 가져온다.
- **코드 분할**
  애플리케이션 규모가 커질수록 번들 역시 커진다. 번들링 되는 파일에는 앱을 만들면서 npm을 통해 다운로드하는 **서드파티 라이브러리**도 포함된다.
  서드파티 라이브러리는 개인 개발자나 프로젝트 팀, 혹은 업체 등에서 개발하는 라이브러리로, 제 3자 라이브러리이다. 서드파티 라이브러리는 플러그인이나 라이브러리 또는 프레임워크 등이 존재하며 이를 잘 사용하면 편하고 효율적인 개발을 할 수 있다. **그러나 사용자에게 다양한 메서드를 제공하므로 코드의 양이 많고, 번들링 시 많은 공간을 차지한다.**
  번들이 거대해지는 것을 방지하기 위한 방법은 코드를 나누는 것이다. **코드 분할**은 런타임에 여러 번들을 동적으로 만들고 불러오는 것이다.
  코드를 분할한다면 애플리케이션의 코드 양을 줄이지 않고도 사용자가 필요하지 않은 코드를 불러오지 않게 하여 애플리케이션의 초기화 로딩에 필요한 비용을 줄여줄 수 있다.
  ```jsx
  /* lodash 라이브러리를 전체를 불러와서 그 안에 들은 메서드를 꺼내 쓰는 것은 비효율적이다.*/
  import _ from 'lodash';

  ...

  _.find([]);

  /* lodash의 메서드 중 하나를 불러와 쓰는 것이 앱의 성능에 더 좋다.*/
  import find from 'lodash/find';

  find([]);
  ```
- **핫 리로딩**
  애플리케이션을 개발할 때는 일반적으로 코드를 조금씩 수정해가며 만든다.
  To do list 기능을 예로 들면 핫 리로딩이 없다면 코드를 수정했을 때 다시 브라우저의 페이지를 새로고침 하고 데이터를 재입력해야 한다.
  이때 핫 리로딩이 있다면 코드 수정 뒤에도 데이터 상태가 사라지지 않고 그대로 유지된 상태로 개발할 수 있다.
  Webpack과 Rollup에서 이러한 기능을 제공한다.
  > **핫 리로딩**
  > : 애플리케이션 개발 시 코드 변경사항을 저장한 후 애플리케이션을 새로고침 없이 실시간으로 반영하는 기능을 뜻한다. 이를 통해 개발자는 개발 중에도 애플리케이션 상태를 유지하면서 UI 변경사항을 빠르게 확인할 수 있다.
  >
  > **React에서 사용하는 방법**
  > React에서 핫 리로딩을 사용하려면 일반적으로 create-react-app이나 다른 빌드 도구와 함께 react-hot-loader 라이브러리를 사용한다.
  >
  > **create-react-app**
  > create-react-app으로 생성된 프로젝트는 기본적으로 핫 리로딩을 지원한다. 즉 추가 설정 없이도 코드를 변경하면 브라우저에 즉시 반영된다.
  >
  > **Custom Setup with Webpack**
  > 만약 Custom Webpack 설정을 사용하는 경우 react-hot-loader를 설치하고 설정해야 한다.
  >
  > 1.  react-hot-loader 설치
  >     `npm install —save-dev react-hot-loader`
  >
  > 2.  Webpack 설정에서 react-hot-loader 추가
  >
  > ```jsx
  > module.exports = {
  >   // ...
  >   module: {
  >     rules: [
  >       {
  >         test: /\.jsx?$/,
  >         exclude: /node_modules/,
  >         use: ["react-hot-loader/webpack", "babel-loader"],
  >       },
  >     ],
  >   },
  >   // ...
  > };
  > ```
  >
  > 3. React 애플리케이션의 entry point에 react-hot-loader/patch 추가
  >
  > ```jsx
  > import React from "react";
  > import ReactDOM from "react-dom";
  > import { AppContainer } from "react-hot-loader";
  > import App from "./App";
  > const render = (Component) => {
  >   ReactDOM.render(
  >     <AppContainer>
  >       <Component />
  >     </AppContainer>,
  >     document.getElementById("root")
  >   );
  > };
  > render(App);
  > // Hot reloading
  > if (module.hot) {
  >   module.hot.accept("./App", () => {
  >     render(App);
  >   });
  > }
  > ```
  >
  > 위와 같이 설정 시 react 애플리케이션에서 핫 리로딩이 활성화되고, 코드 변경사항을 저장할 때 브라우저가 자동으로 업데이트 된다.

## Bundler 종류

![Image](https://github.com/user-attachments/assets/3dc6cf32-118a-4c5b-aff1-b06e0cb259bd)

![Image](https://github.com/user-attachments/assets/582bdf24-0119-46e5-af0b-1d7b1c56a06c)

**Parcel vs Webpack**

|   Bundler   |                                        장점                                        |                                                           단점                                                           |
| :---------: | :--------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------: |
| **Parcel**  |   별도의 구성 옵션 없는 단순한 자동 번들링<br />(소/중형 프로젝트에 적합)<br />    |                   webpack에 비해 구성이 꼼꼼하지 않아 프로젝트의 규모가 커지면 Parcel로는 한계가 있음                    |
| **webpack** | 여러가지 구성 옵션들을 제공하여 매우 꼼꼼한 구성 가능<br />(중/대형 프로젝트 적합) | 규모가 크지 않은 프로젝트에서는 너무 꼼꼼하게 구성 처리를 해서 번들 작업을 하는 것이 배보다 배꼽이 더 큰 작업일 수 있다. |
