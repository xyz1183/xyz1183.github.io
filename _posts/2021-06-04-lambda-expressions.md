---
title: "Lambda Expressions"
categories: 
  - Java
---
JDK 8에 Lambda Expressions가 추가되었다.   
Lambda Expressions로 단일 메서드 인터페이스(함수형 인터페이스)를 간결하게 표현할 수 있다.   

```java
interface Movable{
    void move(String str);
}
```
```java
Movable movable = new Movable() {
    @Override
    public void move(String str) {
        System.out.println("move" + str);
    }
};
```
```java
Movable movable = (str) -> { 
    System.out.println("move" + str); 
};
```
input이 한개면 ()를 생략할 수 있고 output이 한줄이면 {}를 생략할 수 있다. 
```java
Movable movable = str -> System.out.println("move" + str);
```

- - - 
참고  
* <https://multifrontgarden.tistory.com/124?category=471239>

