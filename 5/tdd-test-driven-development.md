# TDD (Test Driven Development)

테스트 코드를 작성할 수 있는 방식을 크게 두가지로 나눌 수 있다.

* TDD (Test Driven Development)
* BDD (Behavior Driven Development)

## TDD

일반적으로 테스트 코드를 먼저 작성하면 TDD 방식으로 인지한다. 하지만 정말 중요한 것은 실패하는 테스트 코드를 작성한 후 바로 `성공하는 테스트 코드`를 작성하는 것이다.&#x20;

이와같이 리팩토링을 안전하게 할 수 있는 환경을 빠르게 구축한 후 코드 퀄리티를 높여가는 기술이다.&#x20;

* 반복적이고 빠른 피드백으로 안정적인 환경에서 코드 품질을 높인다.
  * 동작은 바뀌지 않고 설계만 바뀐다 (내부에 구현되는 코드가 계속 바뀌지만, 스펙은 변경되지 않는것)
  * `green 을 만들기 위해! 죄악을 저질러도 된다`라는 말을 켄트백이 할 만큼 빠르게 성공하는 테스트를 만들어야한다.
* 각 단위의 역할이 단순해지고 명확해진다.
  * 구현보다 인터페이스와 스펙을 먼저 정의해기 때문에 역할이 명확해진다.
  * add(x, y) -> number 이와 같은 시그니처들이 모여 인터페이스가 된다.

## BDD (Behavior Driven Development)

사용자의 행위를 생각하고 테스트하며 개발하는 방식이다. BDD 와 TDD 는 별개의 테스트 코드 작성방식이 아니라 BDD 는 사용자 행위에 따라 TDD 를 잘 작성한 것이다.

![](<../.gitbook/assets/image (5).png>)

추가 자료 : [tv.kakao.com/channel/3693125/cliplink/414004682](https://tv.kakao.com/channel/3693125/cliplink/414004682)

#### 예시코드 :&#x20;

```typescript
const context = describe;

describe('add', () => {
    it('두 숫자의 합을 반환한다.', () => {
       expect(add(1, 2)).toBe(3); 
    });
    
    context('두개의 인자가 주어졌을 때', () => {
       it('두 수의 합을 반환한다.', () => {
       
       })
    });
    
    context('한개의 인자가 주어졌을 때', () => {
       it('동일한 인자 값을 반환한다.', () => {
         expect(add(2)).toBe(2); 
       })
    })
});
```



BDD 방법론은 사용자 행동기반 시나리오로 코드를 검증할 수 있기 때문에 실제 개발환경에서는 BDD 방법론이 더 적합하다고 생각한다. 이렇게 작성된 결과는 개발자뿐만 아니라 기획과 같이 이해관계자들에게 제공하는 기능 명세서로도  활용할 수 있다.&#x20;

물론 유지보수(인수인계)가 용이하다는 것은 말하지 않아도 디폴트!



자바스크립트 기반 테스트를 작성할 수 있는 도구는 크게 3가지가 있다. Jest, mocha, jasmine. 이 중 Jest 를 많이 사용하는 추세이다.&#x20;

jest 의 경우 다른 도구와 달리

* setup 과정이 쉬움
* test runner, test matcher, test mock 프레임워크까지 제공됨

이런 이점이 있어 많이 선택된다.



참고자료 : [https://jestjs.io/docs/api](https://jestjs.io/docs/api)
