# React Testing Library

## React Testing Library

### 개념

* 사용자 입장에서 테스트를 작성할 수 있는 테스팅 라이브러리다. 사용자 입장의 테스트란 행위 주도 테스트(Behavior Driven Test) 를 의미한다. 이는 사용자가 애플리케이션을 이용하는 관점에서 즉, 사용자 시나리오기반 테스트를 작성하는 것이다.&#x20;
* 어떤 컨텐츠가 보이는지, 사용자가 발생시킨 이벤트로 어떤 결과가 나타나는지에 초점을 맞춰 테스트를 작성한다. 이렇게 테스트를 작성하기 위해선 DOM 이 필요한데 jsdom 이라는 라이브러리를 통해 DOM 을 기반으로 테스트가 가능하게 한다.

### 자주 사용하는 matcher

* toEqual : 원시타입을 제외한 데이터 타입을 비교할 때 사용
* toBeTruthy, toBeFalsy
* toHaveLength
* toContain : 배열에 특정값이 존재하는지 비교 (includes 로 생각하면됨)
* toMatch : 정규식 기반 테스트시 사용
* toThrow : 예외 발생 여부 테스트 (인자에 예외 메시지를 넣을 수 있음)

## Given - When - Then 패턴

* given : 준비
* when : 실행
* then : 검증

### Given

* 테스트를 준비하는 과정
* 테스트에 사용하는 변수, 입력 값등을 정의하거나, mock 객체를 정의하는 구문도 given 에 포함

### When

* 실제로 액션이 호출되는 테스트를 실행하는 과정
* 하나의 메서드|함수만 수행하는 것이 바람직함
* 따라서 when 구문이 가장 심플함

### Then

* 테스트를 검증
* 예상한 값, 실제 실행을 통해서 나온 값을 검증



[https://martinfowler.com/bliki/GivenWhenThen.html](https://martinfowler.com/bliki/GivenWhenThen.html)

```jsx
test('TextField', {
    // given 무언가 준비함
    const setFilterText = () => {}
    
    // when
    render((
        <TextField 
            placeholder=''
            filterText='Tester'
            setFilterText={setFilterText}
        />
    ));
    
    // then when 의 결과
    const input = screen.getByLabelText('Search'); //label 이 Search 인 input 이 잡힘
    /*
    - get@@ 의 경우 있으면 ok 없으면 error
    - screen.getByLabelText(/Sear/) -> 정규표현식으로도 활용할 수 있음
    - 여기서 문제점은 무엇일까??
      ㄴ TextField 는 범용적인 컴포넌트인데 Search 라는 라벨이 하드하게 들어가있음
    */
    screen.getByDisplayValue('Tester');
});

const setText = jest.fn();
expect(setText).toBeCalled();
```

## Mocking

* 테스트하는 코드가 의존하고 있는 부분을 가짜(mock)로 대체하는 기법

### jest.fn 사용하기

```jsx
const setText = jest.fn();
setText(1);
setText('a');
setText([1, 2, 3]);

// 목킹한 setText 는 인자로 어떤 것이든 받을 수 있음

// mockReturnValue 을 호출 해 return 값을 만들 수 있음
setText.mockReturnValue('bomee');
console.log(setText()); // bomee

// mockResolvedValue 으로 비동기 상태를 만들 수 있음
setText.mockResolvedValue('async bomee');
setText().then(result => console.log(result)); // async bomee

// mockImplementation 으로 콜백 함수를 넘길 수 있음
setText.mockImplementation(name => `hello, ${name}!`);
console.log(setText('bomee')); // hello, bomee!


// 목킹한 함수는 자신의 호출 상황을 기억하고 있음
expect(setText).toBeCalled();
expect(setText).toBeCalledTimes(6);
expect(setText).toBeCalledWith(/bomee/);
```

## Test Fixture

### 개념

* 테스트 실행을 위해 정의한 정적인 데이터
* 디렉토리 구조

```
fixtures
    ㄴ products.ts // 상품과 관련된 정적 데이터
    ㄴ orders.ts // 주문과 관련된 정적 데이터
```

