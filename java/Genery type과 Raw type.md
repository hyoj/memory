Generic type은 타입을 파라미터로 가지는 클래스(`class<T>`)와 인터페이스(`interface<T>`)를 의미한다.

Raw type은 타입 파라미터가 없는 제네릭 타입을 의미한다.
Raw type은 Generic이 나오기 전(JDK 5.0 이전) 코드와 호환성 보장을 위한 것이다.
(애초에 제네릭으로 정의하지 않은 클래스나 인터페이스에는 Raw Type 이란 것은 없다.)

```java
public class Box<T> {
	public void set(T t) { /*...*/ }
}

```
```java
public static void main(String[] args) {
	Box rawBox = new Box(); // Box는 제네릭 타입이지만 타입 파라미터 없이 생성 (Raw Type)
	Collection boxes = new ArrayList<>(); // Collection Raw type
}
```

Raw type은 타입 선언에서 제네릭 타입 정보가 전부 지워진 것 처럼 동작한다.

