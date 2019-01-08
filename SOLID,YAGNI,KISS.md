## 객체지향 개발 5대 원리 'SOLID'

1. Single responsibility (단일 책임): 하나의 클래스는 하나의 역할을 담당하도록 함
2. Open/closed principle (개방 폐쇄 원칙): 확장에는 개방적, 수정에는 폐쇄적
3. Liskov substitution (리스코프 교체): 객체는 subtype에 관계없이 대체 가능해야 함
4. Interface segregation (인터페이스 분리): 다목적 인터페이스 1개보다 상황에 맞는 다양한 인터페이스 권장
5. Dependency inversion (의존성 역전): 상위 모듈이 하위 모듈에 의존하면 안됨

## YAGNI (You aren't gonna need it)
그건 필요하지 않을거다

- 당장 필요하지 않은 것은 미리 구현하지 말자
- 실제로 코드가 필요하기 전까지는 해당 코드를 작성하지 말자
- "기능이 실제로 필요하기 전까지는 추가하지 않는 것이 좋다" 라는 익스트림 프로그래밍 원칙
- 나중에 쓰일 것 같다는 예측에 따라 만든 것은 실제로는 10% 정도 밖에 쓰이지 않음
- 필요 이상의 기능을 추가하면 설계가 복잡해짐
- 인력은 한정적이므로 현실적 문제에 집중해야 함
- 코드를 빨리 구현하려면 코드를 적게 써라. 오류를 줄이려면 코드를 적게 써라

## KISS 원칙

    "Keep it simple, stupid"
    "Keep it short and simple"
    "Keep is simple and straightforward"

이 디자인 원리는 간단하고, 나중에도 쉽게 이해되는 해결 방법을 최적의 해결책으로 생각한다.
