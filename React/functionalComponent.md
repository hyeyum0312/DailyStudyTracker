# 함수형 컴포넌트 (functional component)

Javascrip 함수 형태로 정의합니다. 
- 심플한 문법 :
    상태(state)나 라이프사이클 없이 props를 전달받아 UI를 반환합니다.
- Hooks : 
    React 16.8이후로 도입된 Hooks를 사용 하여 함수형 컴포넌트에서도 상태(state)와 라이프사이클 기능을 사용할 수 있습니다.
- 무상태 컴포넌트 : 
    초기에는 주로 상태를 가지지 않는 무상태 컴포넌트로 사용되었지만 Hooks덕분에 이제는 상태를 가질 수 있게 되었습니다. 
- 퍼포먼스 : 
    클래스형 컴포넌트보다 약간 더 성능이 좋다고 여겨집니다. (컴파일 시점에 최적화되기 때문)
- 독립적 : 
    함수형태로 컴포넌트를 작성하므로 외부상태에 의존하지 않고 독립적으로 테스트가 가능합니다.


``` javascript

    function greeting(props) {
        return (<h1>안녕하세요 {props.name}님! </h1>)
    }

```


Hooks 사용 예제
```js
import React, {useState} from 'React';

function counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>클릭 하세요 , count: {count}</p>
            <button onClick={()=>{ setCount(count + 1)}}>Click Me !!</button>
        </div>
    )
}

```