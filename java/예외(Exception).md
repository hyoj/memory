# 예외(Exception)
Exception은 크게 RuntimeException / Exception 두가지로 구분된다.

Exception은 컴파일시 발생하는 예외이다.
RuntimeException은 실행 도중 발생하는 예외이다.

Exception은 코드를 작성할 때 이미 예측가능한 예외를 작성할 때 사용한다.
RuntimeException은 발생 할 수도, 발생하지 안할수도 있는 경우에 작성한다.

그래서 Exception을 Checked Exception,
RuntimeException을 Unchecked Exception 이라고도 한다.

## 예외 처리하기
예외처리를 위한 try-catch 문의 기본 구조이다.
finally 구문은 try 문장 수행 중 예외발생 여부에 상관없이 무조건 실행된다.
```java
try { 
	... 
} catch(예외1) {
	...
} catch(예외2) {
	...
} finally { // 어떤 예외가 발생하더라도 반드시 실행되어야 하는 부분

}
```

## 예외 던지기 (throws)
메서드를 호출한 곳에서 예외를 처리하도록 예외를 위로 던질 수 있다.
이를 예외를 뒤로 미룬다고 표현하기도 한다. (예외 뒤로 미루기)

예외를 던지는 방법은 `throws` 구문을 이용한다.

Exception을 처리하는 위치는 매우 중요하다. 프로그램의 수행여부를 결정하기도 하고 트랜잭션 처리와도 밀접한 관계가 있기 때문이다.

---
[[트랜잭션(Transaction)]]