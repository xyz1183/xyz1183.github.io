---
title: "Functional Interface"
categories:
  - Java
---
Java8 java.util.function에서 제공하는 함수형 인터페이스 정리이다.  

<b>1. Consumer&lt;T&gt;</b>  
단일 input을 받고 결과를 반환하지 않는 작업을 나타낸다.
```java
        Consumer<String> consumer = str -> System.out.println(str);
        // method reference: consumer = System.out::println;        
        consumer.accept("abc");
```  
<b>2. Function&lt;T, R&gt;</b>  
단일 input을 받고 결과를 반환하는 함수를 나타낸다.
```java
        Function<String, Integer> function = str -> Integer.parseInt(str);
        // method reference: function = Integer::parseInt;
        Integer result1 = function.apply("1");
```
     
<b>3. Predicate&lt;T&gt;</b>   
단일 input의 부울값 함수를 나타낸다.  
```java
        Predicate<String> predicate = str -> str.equals("abc");
        boolean result2 = predicate.test("bc");
``` 
   
<b>4. Supllier&lt;T&gt;</b>  
공급자를 나타낸다.   
```java
        Supplier<String> supplier = () -> "ABC";
        String result3 = supplier.get();
```  
   
<b>5. UnaryOperator&lt;T&gt;</b>  
input과 동일한 타입의 결과를 생성하는 연산을 나타낸다.    
```java
        UnaryOperator<String> unaryOperator = str -> str.toUpperCase();
        // method reference: unaryOperator = String::toUpperCase;
        String result4 = unaryOperator.apply("abc");
```
     
<b>6. BinaryOpertor&lt;T&gt;</b>  
같은 타입의 두 input에 대한 연산을 나타내며 return 타입도 input의 타입과 같다.
```java
        BinaryOperator<String> binaryOperator = (str1, str2) -> str1 + str2;
        String result5 = binaryOperator.apply("abc", "def");
```  
<b>7. Bi</b>  
prefix로 Bi를 붙여주면 두 개의 input을 받는 함수형 인터페이스가 된다.  
<ul>
  <li>BiConsumer<T, U>, BiFunction<T, U, R>, BiPredicate<T, U></li>  
</ul>
<b>8. Int, Long, Double</b>  
input 타입과 return 타입을 int, long, double로도 지정할 수 있다.  
<ul>  
  <li>DoubleSupplier, IntConsumer, LongFunction&lt;R&gt; 등..</li>
</ul>
Function의 return 타입을 지정할 때는 ToInt, ToLong, ToDouble을 쓴다.  
<ul>
  <li>ToDoubleFunction&lt;T&gt;, IntToLongFunction, ToIntBiFunction<T, U> 등..</li>  
</ul>
