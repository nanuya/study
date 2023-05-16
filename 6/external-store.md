---
description: 리액트 외부에서 상태를 관리하는 방법에 대해 학습하기
---

# External Store

## 관심사의 분리

작은 조각들이 모여 하나의 프로그램을 만든다. 그럼 어떤 기준으로 분리할 수 있을까?

* 기능적으로 나눌 수 있음
* 설계적으로 layered architecture 로 나눌 수 있음 > 사용자를 기준으로 사용자에게 가까운것과 먼것으로 나눔
  * 가장 가까운 것은 UI
  * 비즈니스 로직
  * 데이터 접근/저장

이와같이 각 부분은 하나의 역할, 하나의 관심사로 격리됨으로써 복잡도를 낮춘다.







## Layered Architecture







## Flux Architecture

MVC 대안으로 얘기하지만 패북에서 MVC 를 잘 못 사용하고 있어서 더 복잡도가 높아진 것 같다. 2-way binding 으로 Model <-> View 가 서로 영향을 주는 관계로 사용했기 때문에 복잡해진 것!

그래서 강조되는 개념이 unidirectional data flow 로 단방향으로 처리하는 것!





## useReducer





## useCallback
