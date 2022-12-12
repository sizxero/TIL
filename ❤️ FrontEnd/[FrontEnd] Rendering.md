# 🚩 [FrontEnd] Rendering

## 🚩 Rendering이란?

서버로부터 html, css, javascript 파일 등을 받아 브라우저에 그래픽 형태로 뿌려주는 작업이다.

### 중요 랜더링 경로 (Critical Rendering Path)

![image](https://user-images.githubusercontent.com/51533341/206687910-1aa446c8-08f3-4d26-8819-1919a19babc1.png)

랜더링 엔진의 동작 과정은 다음과 같이 크게 4단계로 이루어져 있다. 각 단계에서 리소스를 로드하는 순서나 작성한 스크립트의 내용에 따라 웹 페이지의 반응 속도가 달라질 수 있기 때문에 최적화를 하는 것이 중요하다.

### ① DOM, CSSOM 생성

![image](https://user-images.githubusercontent.com/51533341/206687982-66c90736-246a-4e06-a116-4db456de3643.png)

서버로부터 HTML과 CSS를 받아 Object Model을 생성한다. DOM(Document Object Model)은 우리가 실제로 사용할 수 있는 HTML 요소의 정보가, CSSOM(CSS Object Model)에는 스타일, 규칙, 선택자 등의 정보가 노드에 들어가게 된다.

### ② Render Tree 생성

![image](https://user-images.githubusercontent.com/51533341/206688038-811ee52c-8fa0-47e8-9a10-009c71257abb.png)

랜더 트리는 위의 DOM과 CSSOM이 합쳐져서 구성된다. 화면에 나타나는 요소들을 결정하는 트리이며, 화면에 그려지지 않는 요소들은 트리에 나타나지 않는다.

### ③ Layout 또는 Reflow

레이아웃 단계에서는 랜더 트리에서 계산되지 않았던 노드들의 크기와 위치, 레이어 간 순서와 같은 정보를 계산하여 좌표에 나타낸다. 이 과정은 HTML의 루트 오브젝트로부터 재귀적으로 실행된다.

### ④ Paint

페인트 단계는 레이아웃 단계를 통해 화면에 배치된 요소들에 색을 입히고 레이어의 위치를 결정하는 단계이다. 이 단계 역시 루트 오브젝트로부터 재귀적으로 실행된다. z-index가 낮은 순서대로 먼저 페인팅 된다.

### ⑤ Reflow and Repaint

자바스크립트에 따른 액션과 이벤트 조작이 있을 시, 그에 영향을 받는 자식 노드나 부모 노드를 포함하여 다시 layout 과정을 수행한다. 이 과정이 reflow이며, reflow 뒤에는 repaint도 다시 일어난다. 이것은 서버와 http 통신을 하고 request와 response를 주고 받은 다음 일어나는 과정이다. 많아지는 reflow, repaint로 인한 re-rendering cost를 해소하기 위해 등장한 것이 ajax, jQuery, React, Angular와 같은 라이브러리/프레임워크이다.


## 🚩 CSR (Client Side Rendering)

![image](https://user-images.githubusercontent.com/51533341/206989618-1cbca077-449e-463e-b30f-21ffca009952.png)


처음 브라우저에서 애플리케이션을 렌더링할 때 비어 있는 html을 응답받고 클라이언트 단에서 자바스크립트를 사용하여 DOM을 조작, 직접 렌더링 하는 것을 의미한다. 서버에서 처리 없이 클라이언트로 보내주기 때문에 자바스크립트가 모두 다운로드 되고 실행이 끝나기 전까지 사용자는 볼 수 있는 것이 없다.

네트워크가 빠를 때, 서버의 성능이 좋지 않을 때, 사용자에게 보여줘야 하는 데이터의 양이 많을 때, 메인 스크립트가 가벼울 때, 웹 어플리케이션에 사용자와 상호작용할 것들이 많을 때 CSR을 사용한다.


## 🚩 SSR (Server Side Rendering)

![image](https://user-images.githubusercontent.com/51533341/206989661-1ed15a2d-fe22-4121-b898-2fe5bffff934.png)

브라우저가 서버에 페이지를 요청하면 서버가 기존에 정의된 데이터로 html을 구성하여 브라우저에 응답하고, 브라우저는 이를 그대로 화면에 렌더링하는 방식이다. 서버에서 이미 렌더 가능한 상태로 클라이언트에 전달되기 때문에, 자바스크립트가 다운로드 되는 동안 사용자는 무언가를 보고 있을 수 있다.

네트워크가 느릴 때, 검색 엔진 최적화가 필요할 때, 최초 로딩이 빨라야 하는 사이트를 개발할 때, 메인 스크립트가 크고 로딩이 매우 느릴 때, 웹 사이트가 상호작용이 별로 없을 때 SSR을 사용한다.


## 🚩 SSG (Static Site Generation)

![image](https://user-images.githubusercontent.com/51533341/206989747-104cd0d8-058f-4158-b94b-86aa9397f0c3.png)

raw 데이터와 템플릿 세트를 바탕으로 완전히 정적인 html 웹 사이트를 생성하는 방법이다. 웹 사이트의 모든 페이지를 미리 렌더링하고 클라이언트의 요청에 따라 페이지를 제공한다. 내용이 거의 변하지 않는 웹사이트인 경우에 SSG를 사용한다.


## 🚩 ISR (Incremental Static Regeneration)

![image](https://user-images.githubusercontent.com/51533341/206989784-384083f4-72f7-4137-932e-c06473a3049a.png)
전체 사이트를 재빌드할 필요 없이 페이지별로 정적 생성을 한다. 블로그나 개인 웹사이트처럼 콘텐츠가 동적이지만 자주 변경되지 않는 사이트의 경우 ISR를 사용한다.


## 📚 References

[https://yozm.wishket.com/magazine/detail/1338/](https://yozm.wishket.com/magazine/detail/1338/)

[https://velog.io/@jeromecheon/프론트엔드라면-반드시-알아야-할-Rendering과-세가지-개념-CSR-SSR-SSG](https://velog.io/@jeromecheon/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C%EB%9D%BC%EB%A9%B4-%EB%B0%98%EB%93%9C%EC%8B%9C-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-Rendering%EA%B3%BC-%EC%84%B8%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-CSR-SSR-SSG)

[https://proglish.tistory.com/216](https://proglish.tistory.com/216)