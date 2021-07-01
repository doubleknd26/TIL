# 파이썬은 어떻게 동작하는가 (DRAFT)


1. .py 확장자로 실행 가능한 파이썬 코드를 만든다. e.g) python app.py
2. python app.py 를 실행하면 다음과 같은 일이 발생한다.
  -> .py 파일을 바이트 코드 상태로 컴파일 한다.
  -> PVM (Python Virtual Machine) 이라 하는 파이썬 실행 환경에 바이트 코드를 전달한다.


CPython -> 파이썬 인터프리터 & 컴파일러. 우리가 작성하는 python 코드를 bytecode로 컴파일해준다. 그리고 그 bytecode 를 PVM 에서 실행하는 구조이다.


PVM 은 파이썬의 런타임 엔진 입니다. 파이썬 시스템의 일부이기 때문에 별도의 설치가 필요하지 않고, 항상 존재 합니다.


.py 파일을 실행하면 .pyc 라는 파일이 생성되는데 이것이 CPython이 컴파일한 bytecode가 들어있는 것이다. 그 다음 .pyc를 interpret 하는 것도 CPyton이다.

.pyc 파일은 파이썬 3.2 버전 이전에는 .py 파일과 같은 경로에 생성되고
3.2 이후 버전에서는 __pycache__ 디렉터리 아래에 생성 됩니다.


CPython 이외에도 몇가지 컴파일러가 더 있다. 
Jython
- Java 바이트 코드로 만들어 JVM 에서 실행할 수 있도록 한다.
- .py 파일을 .class 파일로 컴파일 한다.


PyPy
- Python으로 구현된 컴파일러.
- JIT 컴파일을 도입하여 CPython 보다 빠르다. (JIT(just-in-time) 컴파일 이란 프로그램을 실행하기 전에 컴파일 하는 대신, 프로그램을 실행하는 시점에서 피료한 부분을 즉석으로 컴파일하는 방식.)