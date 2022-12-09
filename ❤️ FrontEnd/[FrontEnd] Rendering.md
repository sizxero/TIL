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