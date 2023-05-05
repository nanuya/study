# REST API

* 필딩 제약 조건 4가지가 있음
  * Richardson 성숙도 레벨을 정의함.
  * 보통은 4가지 모두 만족하지 않고, Resource 와 HTTP Verb 만 도입하는 수준으로 사용
  *    Resource 를 쓴다? 하나의 url 에 대해 하나의 resource\
    /posts 라는 리소스에 대해 뭔가를 한다

### READ&#x20;

* Collection(복수)
* Item(단수)

컬렉션 패턴이라고 함.

* GET /products
* GET /products/{id}
* POST /products -> 상품추가
* PUT /products -> 없으면 생성, 있으면 덮어씀
* PATCH /products/{id} -> 일부만 업데이트(특정 상품 정보 변경)
* DELETE /products{id} -> 특정 상품 삭제

