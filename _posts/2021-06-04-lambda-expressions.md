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
  
### 행위 파라미터화 (Behavior Parameterize)
```java
List<Fruit> extractApple(List<Fruit> fruits){
    List<Fruit> resultList = new ArrayList<>();
    for(Fruit fruit : fruits){
        if("apple".equals(fruit.getName())){
            resultList.add(fruit);
        }
    }

    return resultList;
}

List<Fruit> extractRed(List<Fruit> fruits){
    List<Fruit> resultList = new ArrayList<>();
    for(Fruit fruit : fruits){
        if("red".equals(fruit.getColor())){
            resultList.add(fruit);
        }
    }

    return resultList;
}
``` 
위의 코드는 if문을 제외하면 모두 중복된다.  
Predicate를 활용해 아래와 같이 하나로 합칠 수 있다. 
```java
static List<Fruit> extractFruitList(List<Fruit> fruits, Predicate<Fruit> predicate){
    List<Fruit> resultList = new ArrayList<>();
    for(Fruit fruit : fruits){
        if(predicate.test(fruit)){
            resultList.add(fruit);
        }
    }

    return resultList;
}
```
호출하는 과정은 아래와 같으며 람다식으로 간결하게 바꿀 수 있다.  
```java 
List<Fruit> appleList = extractFruitList(fruits, new Predicate<Fruit>() {
    @Override
    public boolean test(Fruit fruit) {
        return "apple".equals(fruit.getName());
    }
});

List<Fruit> redList = extractFruitList(fruits, new Predicate<Fruit>() {
    @Override
    public boolean test(Fruit fruit) {
        return "red".equals(fruit.getColor());
    }
});
```
```java
List<Fruit> appleList = extractFruitList(fruits, fruit -> "apple".equals(fruit.getName()));
List<Fruit> redList = extractFruitList(fruits, fruit -> "red".equals(fruit.getColor()));
```

- - - 
참고  
* <https://multifrontgarden.tistory.com/124?category=471239>

