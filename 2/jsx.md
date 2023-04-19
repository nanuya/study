# JSX

## JSX 란?

> `react` 부산물로 `javascript`를 확장한 문법이다. `react` 뿐만 아니라 다른 언어와도 함께 사용할 수 있다.

### JSX 의 특징

* 자바스크립트를 `XML` 같은 문법으로 확장했기 때문에 생김새가 익숙하다.
* `JSX` 를 실행하기 위해서는 `babel`이나 `swc` 같은 트랜스파일러가 필요하다.
  * `JSX` 코드 \
    `<Greeting name="bomee" />`
  *   `트랜스파일된 코드`

      `React.createElement(Greeting, { name: "bomee" });`

그렇다면, `React` 를 사용하려면 `JSX` 사용이 필수일까? 그렇지 않다. `createElement` 라는 `React` 가 제공하는 `api` 를 사용할 수 있다. 심지어 내가 만든 커스텀 `createElement` 를 사용할 수 있다.

아래 조금 더 복잡한 예시를 보자.

```javascript
// JSX 코드
<div>
  <p>Count: {count}!</p>
  <button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>
```

```javascript
// 변환 코드
React.createElement(
  "div",
  null,
  React.createElement("p", null, "Count: ", count, "!"),
  React.createElement("button", { type: "button", onClick: () => setCount(count + 1) }, "Increase")
);
```

요즘처럼 복잡한 웹페이지를 `JSX` 코드 없이 `createElement` api 를 사용해 만들거나 직접 `document` api 를 활용해 만든다고 상상해보자. 🤯

가벼운 예로 아래 api 로 돔을 셀렉해 제어한다고 생각해보자

`querySelector vs getElementBy`&#x20;

* querySelector: 이 친구는 `NodeList` 를 반환한다. 즉, 참조를 끊어버리기 때문에 선택된 돔의 변화가 바로바로 돔에 반영되지 않는다.
* `getElementBy`: 이 친구는 `HTMLCollection` 을 반환한다. 참조가 살아있기 때문에 선택된 돔의 변화가 실시간으로 반영되어 버린다.

제일 많이 사용되는 돔 셀렉 api 인데 벌써부터 복잡하다.

이렇게 JSX 는 복잡한 DOM api 핸들링을 개발자가 아닌 JSX 가 제어권을 가져 대신 처리해주는 문법적 설탕이다.

> ( 문법적 설탕이라고하면 가볍게 느껴지는게 있어서 그런지 사실, 난 `JSX` 가 복잡한 DOM api 를 선언적으로 사용할 수 있게 잘 만들어준 라이브러리처럼 느껴진다.&#x20;
>
> `jquery` 도 라이브러리라고 하는데 그 친구보다 훨씬 선언적으로 `DOM api` 를 사용하게 해주지 않는가?&#x20;
>
> 근데 왜 이친구는 문법적 설탕으로 얘기하는걸까 👀 )

이런 문법적 설탕인 `JSX` 를 우린 항상 필수인 것 처럼 사용하는 이유는 무엇일까?\
바로 `유지보수가 용이하기 때문이다.`





## 정리!

JSX 는 다루기 복잡한 DOM api 의 제어권을 내부에 숨긴다. 이 덕분에 사용하는 입장에서는 더 이상 불필요한 `어떻게 돔을 제어할 것인가` 에 대한 내용을 담지 않아도 되기 때문에 난 `무엇을 할거야!` 에 대해 초점을 맞춰 코드를 작성하면 된다.

즉, JSX는 복잡한 DOM api 제어권을 가져감으로써 사용자에게 선언적 프로그래밍이 가능하도록 도와주는 문법이다!



### 어려운점!

선언적 프로그래밍 이라는 개념이 아직 와닿지 않는다. 어떻게 보다는 `무엇을 하는가`에 초점을 맞춘다고 하는데.. 그게 아직 잘 모르겠다.. 간단하게 이해한 내용으로 아래 예시를 작성해본다.

*   목표: 주어진 숫자배열에서 짝수만 얻기

    \
    여기서 난 그냥 짝수만 얻으면 된다. 그런데 아래 코드를 작성하기 위해서 다음과 같은 생각의 단계를 거쳤다.\
    \- 주어진 숫자배열을 어떤 기준으로 반복할까\
    \- 반복은 어느정도까지 해야할까\
    \- 반복문에서 사용되는 현재 숫자는?\
    \- 짝수면 어디다 담지?\
    난 짝수만 알면되는데 다른 고민사항이 더 많다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = [];

for (let i = 0; i < numbers.length; i++) {
  const currentNumber = numbers[i];
  
  if (currentNumber % 2 === 0) {
    evenNumbers.push(currentNumber)
  }
}

console.log(evenNumbers);
```

&#x20;선언적으로 작성하게 되면?

`(number % 2) === 0` 짝수만 얻기! \
목표였던 `주어진 배열에서 짝수만얻기` 딱 요 부분만 코드로 작성하면된다. 나머진 걍 선언적 api 를 사용함

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(number => (number % 2) === 0);
console.log(evenNumbers);
```

아직 이해한 수준은 딱 이정도 수준이다.
