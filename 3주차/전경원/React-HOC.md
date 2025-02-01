# HOC

# 고차 컴포넌트(HOC)는 무엇인가

고차 컴포넌트(HOC, Higher Order Component)는 컴포넌트 로직을 재사용하기 위한 React 기술 중 하나다.

고차 컴포넌트는 React API의 일부가 아니며, React의 구성적 특성에서 나오는 패턴이다.

구체적으로, 고차 컴포넌트는 컴포넌트를 가져와 새 컴포넌트를 반환하는 함수이다.

```jsx
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

> 컴포넌트는 props를 UI로 변환하는 반면, 고차 컴포넌트는 컴포넌트를 새로운 컴포넌트로 변환한다.

# 예시

```jsx
import React, { useEffect, useState } from "react";

export default function withLoading(Component) {
  const WithLoadingComponent = (props) => {
    const [loading, setLoading] = useState(true);

    useEffect(() => {
      const timer = setTimeout(() => setLoading(false), 1000);

      return () => clearTimeout(timer);
    }, []);
  };

  return loading ? <p>로딩 중...</p> : <Component {...props} />;
}
```

```jsx
import React from "react";
import withLoading from "./withLoading";

function Button() {
  return <button>버튼</button>;
}

export default withLoading(Button);
```
