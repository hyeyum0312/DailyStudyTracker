# React JSX, Virtual DOM

## JSX문법이란?


JSX(JavaScript XML)는 React에서 사용하는 문법 확장으로, JavaScript 코드 안에 XML 같은 태그를 사용할 수 있게 해줍니다. 
이는 React 컴포넌트의 UI를 정의하는 데 매우 유용합니다. JSX는 HTML과 비슷한 구문을 사용하지만, JavaScript 코드 내에서 직접 사용할 수 있습니다. 
JSX를 사용하면 코드가 더 직관적이고, 구조화되어 있으며, 가독성이 좋아집니다.

**주의점**

JSX는 React.createElement() 함수를 호출하는 JavaScript 코드로 변환됩니다. 
따라서, JSX 코드를 사용하기 위해서는 Babel과 같은 트랜스파일러를 통해 변환이 필요합니다.

```javascript
const element = <h1 className="greeting">Hello, world!</h1>;
// 위 코드는 아래와 같이 변환됩니다.
const element = React.createElement('h1', { className: 'greeting' }, 'Hello, world!');
```


---
## Virtual DOM

**Virtual DOM이란?**


Virtual DOM은 실제 DOM(Document Object Model)의 가벼운 사본입니다. 
메모리에 존재하며, 실제 DOM과 같은 구조를 가지고 있습니다. 리액트는 Virtual DOM을 사용하여 UI 변경 사항을 추적하고 효율적으로 업데이트합니다.



**왜 Virtual DOM을 사용하는가?**


실제 DOM 조작은 느리고 비용이 많이 드는 작업입니다. 
특히, 많은 요소를 한 번에 업데이트하거나 복잡한 트리를 조작할 때 더욱 그렇습니다. 
Virtual DOM을 사용하면 **변경 사항을 메모리에서 먼저 처리**한 후, **필요한 부분만 실제 DOM에 반영하므로 성능이 크게 향상**됩니다.


**Virtual DOM의 작동 방식**


- <span color="blue">Initial Render</span>:
초기 렌더링 시, 리액트는 Virtual DOM에 컴포넌트 구조를 만들고, 이를 기반으로 실제 DOM을 생성합니다. 이 단계에서는 Virtual DOM과 실제 DOM이 일치합니다.


- <span color="blue">업데이트 과정</span>:
1. State 변화 감지: 
    컴포넌트의 상태(state)나 속성(props)이 변경되면, 리액트는 새로운 Virtual DOM을 생성합니다. 이는 변경된 상태를 반영한 새로운 트리 구조를 메모리에 만듭니다.
2. Virtual DOM 비교: 
    리액트는 이전 Virtual DOM과 새로운 Virtual DOM을 비교하여 차이점을 찾습니다. 이 과정은 "diffing"이라고 합니다.
3. 패치(patching): 
    리액트는 차이점(변경된 부분)만 실제 DOM에 반영합니다. 이를 통해 전체 DOM을 다시 그리는 것이 아니라, 필요한 부분만 업데이트하므로 성능이 크게 개선됩니다.


## Virtual DOM의 장점

- 성능 최적화: 변경된 부분만 업데이트하므로, 전체 DOM을 다시 그리는 것보다 훨씬 빠릅니다.
- 추상화된 DOM 조작: 개발자는 직접 DOM 조작을 하지 않고, 리액트가 이를 대신 처리하므로 **코드가 더 간결하고 유지보수하기 쉽습니다.**
- Cross-Platform: Virtual DOM은 브라우저 환경뿐만 아니라, React Native와 같은 모바일 환경에서도 사용할 수 있습니다.

