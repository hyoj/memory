# 쓰레드(Thread)
동작하고 있는 프로그램을 프로세스(Process)라고 한다.
보통 한 개의 프로세스는 한 가지의 일을 하지만, 쓰레드를 이용하면 한 프로세스 내에서 두 가지 또는 그 이상의 일을 **동시에** 할 수 있다.

## 쓰레드 생성하기
### 1. Thread 상속하기
```java
public class Sample extends Thread {
	int seq;
	public Sample(int seq) {
		this.seq = seq;
	}
	
	@Override
	public void run() {// Thread를 상속해서 run 메서드를 오버라이딩한다.
		System.out.println(this.seq+" thread start.");
		
		try {
			Thread.sleep(1000); 
		} catch(Exception e) { } 
		
		System.out.println(this.seq+" thread end.");
	}

	public static void main(String[] args) {
		for (int i = 0; i < 10; i++) { // 총 10개의 쓰레드를 생성하여 실행한다. 
			Thread t = new Sample(i); 
			t.start(); // Thread를 상속했기 때문에 start() 호출 시 run 메서드가 내부적으로 수행된다.
		}
		
		System.out.println("main end."); // main 메소드 종료
	}
}
```

### 2. Runnable 인터페이스 구현하기
Thread의 생성자로 Runnable 인터페이스를 구현한 객체를 넘길 수 있다.
```java
public class Sample implements Runnable {
	int seq;
	public Sample(int seq) {
		this.seq = seq;
	}

	@Override
	public void run() { // Runnable 인터페이스는 run 메서드를 구현하도록 강제한다.
		System.out.println("thread run.")
	}

	public static void main(String[] args) {
		for (int i = 0; i < 10; i++) { 
			Thread t = new Thread(new Sample(i)); // Runnable 인터페이스를 구현한 객체를 넘기는 방식 적용
			t.start(); 
		}
		
		System.out.println("main end.");
	}
}
```

쓰레드를 여러개 실행시켜보면 순서에 상관없이 동시에 실행된다.
또, 쓰레드가 종료되기전에 main 메서드가 먼저 종료될 수도 있다.

### 3. 익명 클래스 사용하기
```java
public class ThreadTest {
	public static void main(String[] args) {
		new Thread() {
			public void run() {
				System.out.println("thread run.")
			}
		}.start();
	}	
}
```

### 4. 람다식으로 Runnable 구현하기
```java
public class ThreadTest {
	public static void main(String[] args) {
		new Thread(() -> {
			System.out.println("thread run.")
		}).start();
	}	
}
```

## Join
쓰레드가 종료된 후 그 다음 로직을 수행해야 할 때는 꼭 join 메서드를 사용해야한다.

생성된 쓰레드를 담아두고, 담긴 각각의 thread에 join 메서드를 호출하여 쓰레드가 종료될 때 까지 대기할 수 있다.
```java
...
	public static void main(String[] args) {
		ArrayList<Thread> threads = new ArrayList<>();
		for(int i=0; i<10; i++) {
			Thread t = new Sample(i);
			t.start();
			threads.add(t); // 쓰레드 담아두기
		}

		for(int i=0; i<threads.size(); i++) {
			Thread t = threads.get(i);
			try {
				t.join(); // t 쓰레드가 종료할 때까지 기다린다.
			} catch(Exception e) { }
		}
		
		System.out.println("main end.");
	}
...

```


---
[07-05 쓰레드(Thread) - 점프 투 자바 (wikidocs.net)](https://wikidocs.net/230)

[[Java] 자바 쓰레드 생성(Thread, Runnable) (tistory.com)](https://math-coding.tistory.com/171)

