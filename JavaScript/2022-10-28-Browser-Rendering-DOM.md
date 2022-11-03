# 브라우저 렌더링과 DOM

# 렌더링

<aside>
💡 HTML, CSS, JS 등 개발자가 작성한 문서가 브라우저에서 출력되는 과정

</aside>

- 브라우저는 렌더링을 수행하는 렌더링 엔진을 가진다.
    - 크롬 - 블링크(Blink)
    - 사파리 - 웹킷(Webkit)
    - 파이어폭스 - 게코(Gecko)

### 브라우저 구조

![스크린샷 2022-10-28 오후 4.35.33.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/67472d7e-3546-442c-ad35-2ea9d7bba9b3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-10-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4.35.33.png)

## 렌더링 과정

<aside>
💡 사용자가 브라우저 통해 웹 사이트에 접속하면, 서버로부터 HTML, CSS 등 웹 사이트에 필요한 리소스를 다운로드 받음

</aside>

- 이때, 브라우저가 페이지를 렌더링하기위해선 HTML → DOM, CSS → CSSOM 트리를 생성해야한다.

## DOM

<aside>
💡 Document Object Model의 약자로, HTML과 XML 문서의 프로그래밍 인터페이스를 의미

</aside>

- HTML은 브라우저에서 실행될 수 있게 DOM Tree로 파싱되고, 이를 바탕으로 렌더링이 된다.

### 1-1. DOM 트리 생성

> HTML 코드가 DOM 트리로 변환되는 과정
> 

브라우저는 HTML 마크업을 처리할 때마다 아래의 모든 단계를 수행한다.

1. 변환 : 브라우저가 HTML의 원시 바이트 읽어와 HTML에 정의된 인코딩(ex. UTF-8)에 따라 개별 문자로 변환
2. 토큰화 : 브라우저가 문자열을 W3C 표준에 지정된 고유 토큰으로 변환
3. 렉싱 : 방출된 토큰은 해당 속성 및 규칙을 정의하는  “객체”로 변환
4. DOM 생성 : HTML 마크업에 정의된 여러 태그 간의 관계를 해석해 트리 구조로 연결
    
    ![DOM 트리 생성 과정](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/05f0f81f-28b3-45c7-b5c8-bc0ac477afd7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-11-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.21.34.png)
    
    DOM 트리 생성 과정
    

### 1-2. CSSOM 트리 생성

- HTML 마크업 내에 직접(inline) 스타일 선언도 가능하나, head 태그에 외부(external) css 파일을 참조하거나, head 태그에 style 태그(internal)를 정의할 수 있다.
- HTML과 마찬가지로 외부(external) css 파일에 정의된 스타일과 스타일 태그에 작성된 스타일을 브라우저가 이해하고 처리할 수 있는 형식으로 변환해야 함
- DOM 트리를 생성하는 과정과 동일한 과정으로 CSSOM 트리를 생성한다.
    
    ![CSSOM 트리](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90767344-25f8-4907-9f3e-2471445cdc58/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-11-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.23.28.png)
    
    CSSOM 트리
    

### 2. 렌더링 트리(Rendering Tree)

DOM 트리와 CSSOM 트리가 만들어지면, 이 둘을 결합해 렌더링 트리를 생성한다. 렌더링 트리에는 페이지를 렌더링 하는데 필요한 노드만 포함된다.

![스크린샷 2022-11-03 오후 12.24.08.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e4dd526a-cce6-4822-afc5-1b6927c05b82/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-11-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.24.08.png)

### 3. 레이아웃(Layout) 단계

레이아웃 단계에서는 뷰포트 내에서 각 요소의 정확한 위치와 크기를 정확하게 캡처하는 Box 모델이 출력된다. 모든 상대적인 측정값은 화면에서 절대적인 픽셀로 변환된다.

![스크린샷 2022-11-03 오후 12.25.39.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f405354-cb00-4c7c-80b4-fe2824f198d8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-11-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.25.39.png)

### 4. 페인팅 단계

마지막으로는 렌더링 트리의 각 노드를 화면의 실제 픽셀로 변환한다. 레이아웃 단계에서 모든 계산이 완료가 되면, 화면에 요소들을 그린다. 이 단계를 ‘페인팅’ 또는 ‘래스터화’ 라고 한다.

이미 레이아웃 단계에서 각 노드들의 위치/크기/색상 등 스타일이 모두 계산이 되었기 때문에 화면에 실제 픽셀로 변환이 가능하다.

## 리플로우 (Reflow) , 리페인트 (Repain)

기존 요소에 변경 사항이 생겼다해서 항상 리플로우(Reflow)-리페인트(Repaint) 과정이 일어나는 것은 아님. 레이아웃에 영향이 미치지 않는 단순한 색상 변경 같은 변경사항은 리플로우 수행 없이 바로 리페인트만 수행. 

단, 리플로우가 일어나면 리페인트는 반드시 일어남!

### `리플로우`

> 변경사항 반영위해, 렌더링 트리 생성 및 레이아웃 과정 재수행
> 
- 사용자 웹 페이지 첫 접속시, 렌더링 과정 거쳐 화면에 모든 요소 그려짐
- 사용자의 다양한 액션 수행에 의해 발생되는 이벤트로, 새로운 HTML 요소 추가나 기존 요소의 스타일 변경 발생
- 이러한 변경 통해 영향을 받게되는 모든 노드에 대해, 렌더링 트리 생성과 레이아웃 과정 재실행

### `리페인트`

> 리플로우된 결과를 화면에 다시 그리기위해 페인팅 단계 재수행
> 

### 리플로우와 리페인트 발생 대표 속성

- 리플로우 : position, width, height, margin, padding, border, border-width, font-size, font-weight, line-height, text-align, overflow
- 리페인트 : background, color, text-decoration, border-style, border-radius

## Reference

[https://medium.com/개발자의품격/브라우저의-렌더링-과정-5c01c4158ce](https://medium.com/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EB%A0%8C%EB%8D%94%EB%A7%81-%EA%B3%BC%EC%A0%95-5c01c4158ce)

[https://programming119.tistory.com/236](https://programming119.tistory.com/236)
