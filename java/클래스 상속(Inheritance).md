# 클래스 상속(Inheritance)
자바에는 부모 클래스의 기능을 그대로 물려받을 때 사용할 수 있는 상속(Inheritance) 기능이 있다.

일반 클래스는 단일상속만 가능하다.

## 자바에서 클래스 상속하기
클래스 상속을 위해서는 `extends` 키워드를 사용한다.
```java
class Animal {
	String name;
	void setName(String name) {
		this.name = name;
	}
}

class Dog extends Animal {
}

```

Dog 클래스가 Animal 클래스보다 좀 더 많은 기능을 가질 수 있게 만들 수 있다. 그래서 부모 클래스의 기능을 확장(extends)한다고 표현한다.
```java
class Dog extends Animal {
	void sleep() {
		// sleep...
	}
}
```

## IS-A 관계
Dog 클래스는 Animal 클래스를 상속했다. 즉, Dog는 Animal의 하위 개념이다. 이런 경우 Dog는 Animal에 포함되기 때문에 "개는 동물이다"라고 표현할 수 있다.

자바는 이러한 관계를 `IS-A` 관계라고 표현한다.
즉, "Dog is a Animal"과 같이 말할 수 있는 관계이다.
```java
Animal dog = new Dog(); // Dog is a Animal
```

주의 !
Dog 클래스에만 존재하는 메서드는 사용할 수 없다.

---
[[용어/상속(Inheritance)]]
[[Object 클래스]]
