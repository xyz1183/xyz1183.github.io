---
title: "Try-with-resources"
categories: 
  - Java
---
JDK 1.7에 Try-with-resources가 추가되었다. 
	
```java
    try (
        Socket socket = new Socket("localhost", 8000)));
        BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        PrintStream out = new PrintStream(socket.getOutputStream())
    ) {
	...
    } catch (IOException e) {
        ...
    }
```
위와 같이 코드 작성 시 try catch문 종료 후 socket, in, out의 close()가 호출된다. 
() 안에 들어갈 수 있는 객체는 java.lang.AutoCloseable 인터페이스의 구현체이다. 
```java
public interface AutoCloseable {
    void close() throws Exception;
}
```
참고
* BufferedReader의 close()는 InputStreamReader의 close()를, InputStreamReader의 close()는 InputStream의 close()를 호출한다. PrintStream의 close()도 마찬가지이다. 
* java.io.Closeable 인터페이스는 java.lang.AutoCloseable을 상속받는다.  
