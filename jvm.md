# jvm

### 1. 동작순서

- 프로그램이 실행되면 os로부터 프로그램이 필요한 메모리를 할당받는다.

- jvm은 용도에 따라 여러 영역으로 나누어 관리한다.

- 자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킨다.

- class Loader를 통해 calss파일들을 jvm으로 로딩한다.

- 로딘된 class파일들은 exceution engine을 통해 해석된다.

- 해석된 바이트코드는 runtime data areas에 배치되어 실질적인 수행이 이루어지게 된다.

  이러한 실행과정 속에서 jvm은 필요에 따라 스레드 싱크로나이제션(thread synchronization)과 GC같은 관리 작업을 수행한다. 

### 2. JVM 구성

#### 2.1. Class Loader

