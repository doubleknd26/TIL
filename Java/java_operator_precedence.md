# 논리 연산자 우선순위


```java
public class Main {
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

위 코드의 결과는 다음과 같다
```
A
Hello world!

```

나는 b() -> c() -> a() 순서로 실행될거라고 생각했다. 왜냐면 &&가 || 보다 우선순위가 높으니까 그런데, a() 만 실행됐다. 이유가 뭘까? 아래 연산을 살펴보자.

```
a() || b() && c() 
```

이 연산에서 연산자 우선순위를 적용하면 다음과 같다.

```
a() || (b() && c())
```

&&의 피연산자들이 우선적으로 계산되어야 하니까 괄호로 묶어줬다. 연산자 우선순위에 대한 영역은 여기까지다. 더이상 연산자 우선순위를 따져야 할 b() 같은 존재가 없기 때문이다. 이때부터는 연산자 우선순위의 영역이 아닌, 연산 순서(Evaluation Order) 에 대한 영역이다. 기본적으로 자바는 피연산자가 왼쪽에서 오른쪽으로 연산되는 것을 보장한다. 이에 따라 a() 가 먼저 수행이 되고, a()가 true 이기 때문에 위와 같은 결과가 나오는 것이다.



reference: 
*https://stackoverflow.com/questions/21557124/logical-operator-precedence-in-java
https://docs.oracle.com/javase/specs/jls/se7/html/jls-15.html#jls-15.7*