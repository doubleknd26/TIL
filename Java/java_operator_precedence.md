# 논리 연산자 우선순위 (DRAFT)

&& 가 || 보다 우선순위가 높다.
근데, 아래 코드를 실행해보면 a 만 실행된다.

```java
//Please don't change class name 'Main'

class Main {

  public static void main(String[] args) {
    if (a() || b() && c()) {
			System.out.println("Hello world!");
		}
  }
	
	private static boolean a() {
		System.out.println("A");
		return true;
	}
	
	private static boolean b() {
		System.out.println("B");
		return true;
	}
	
	private static boolean c() {
		System.out.println("C");
		return true;
	}
}

```