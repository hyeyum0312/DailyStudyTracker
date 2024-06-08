# 이벤트 처리 (Handling Events)
React에서는 DOM 요소에서 이벤트를 처리할 수 있습니다. 
React의 이벤트 처리 방식은 DOM 요소의 이벤트 처리와 몇 가지 차이점이 있습니다:


## CamelCase 이벤트 핸들러:
HTML에서는 소문자 이름을 사용하지만, React에서는 CamelCase로 작성합니다.

``` javascript
<button onClick={handleClick}>Click me</button>
```

## 함수 참조 전달:
JavaScript 코드에서 문자열을 전달하는 대신, 함수 참조를 전달합니다.

```javascript
function handleClick() {
  alert('Button was clicked!');
}

<button onClick={handleClick}>Click me</button>
```

## 이벤트 객체:
React 이벤트는 SyntheticEvent라는 합성 이벤트 객체를 전달합니다. 
이 객체는 브라우저 간 호환성을 유지하면서, 네이티브 이벤트와 유사한 API를 제공합니다.

```javascript
function handleClick(e) {
  e.preventDefault();
  console.log('The link was clicked.');
}

<a href="#" onClick={handleClick}>Click me</a>
```

## this 바인딩:
클래스 컴포넌트에서 이벤트 핸들러는 기본적으로 this가 정의되지 않으므로, 바인딩을 수동으로 해줘야 합니다. 
이를 위해 바인딩하거나, 클래스 필드 문법을 사용합니다.
```javascript
// 바인딩 방법 1: 생성자에서 바인딩
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    // 이 바인딩 없이는 `this`가 `handleClick` 내에서 undefined입니다.
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

// 바인딩 방법 2: 클래스 필드 문법 사용
class Toggle extends React.Component {
  state = {isToggleOn: true};

  handleClick = () => {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  };

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}
```