# Object
자바에서 만드는 모든 클래스는 Object 클래스를 상속받는다.  
사용자가 정의한 클래스는 모두 아래처럼 Object 클래스를 상속한 것과 동일하다.

```java
class Animal extends Object {
	String name;
	
	void setName(String name) {
		this.name = name;
	}
}
```

하지만 굳이 상속하도록 코딩하지 않아도 자바에서는 자동으로 Object 클래스를 상속받게끔 되어 있다.

따라서 자바에서 만드는 모든 객체는 Object 자료형으로 사용할 수 있다.
```java
Object Animal = new Animal(); // Animal is a Object
```