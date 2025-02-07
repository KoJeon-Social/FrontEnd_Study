# document

브라우저에서 사용할 수 있는 object

HTML에서 값을 가져오고 바꿀 수 있다.

- document .getElementById() : html에 있는 id 값을 불러올 수 있다.
- element.innerText = “Hello” 로 JS에서 값 바꾸기 가능
- className으로 class 값 변경 가능

querySelector() 와 getElementById()는 같은 일을 하지만 후자는 하위요소를 가져오지 못하기 때문에 전자를 많이 사용

### querySelector

class, id 전부 사용 가능하며 해당하는 태그들을 쓰면 해당 클래스/id 특정 태그들만 가져올 수 있다.

만약 동일한 class가 있다면 첫 번째 element만 가져온다.

전부 가져오고 싶으면 querySelectorAll 사용

### event

어떤 행위를 하는 것

모든 event는 js가 listen할 수 있다.

- eventListener : event를 listen함 → JS에게 무슨 event를 listen하고 싶은 지 알려줘야 함
- addEventListener() : 어떤 이벤트를 listen 할 거니까 무언가를 해줘야 함

> 팁 : 중복되는 건 상수로 선언해서 사용하기

### toggle

class name이 존재하는지 확인하고, 존재하면 class name을 제거하고 존재하지 않으면 class name을 추가한다.
