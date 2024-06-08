# 조건부 렌더링 (Conditional Rendering)
조건부 렌더링은 특정 조건에 따라 다른 컴포넌트를 렌더링하는 방법입니다. 
JavaScript의 조건문을 사용하여 이를 구현할 수 있습니다. 


```javascript
// if문 
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please sign up.</h1>;
  }
}

// 삼항연산자
function Greeting(props) {
  return props.isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please sign up.</h1>;
}

// 논리 &&연산자
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 && (
        <h2>You have {unreadMessages.length} unread messages.</h2>
      )}
    </div>
  );
}

// 즉시실행
function Greeting(props) {
  return (
    <div>
      {(() => {
        if (props.isLoggedIn) {
          return <h1>Welcome back!</h1>;
        } else {
          return <h1>Please sign up.</h1>;
        }
      })()}
    </div>
  );
}
```