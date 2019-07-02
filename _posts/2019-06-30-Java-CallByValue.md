---
layout: post
title: Java Call by What? Pass by What?
category: Java
tags: [Java]
---

# Java는 항상 'Call by Value'
<br/>
C언어 수업에서 Call by value와 Call by reference를 배웠던 것 같다.<br>
이후 다른 수업과 책에서는 따로 언급이 없어서 다른 언어도 위의 개념으로 이해하고 있었는데<br>
너무 합리적 의심없이 살았다..<br>
<br/><br/>

## Pass by = Call by
일단 용어가 너무 많다 생각했는데 동의어예요.<br/>
함수 호출시 전달되는 매개변수가 value인지 reference인지 차이이므로<br/>
'Call'은 메소드 호출에서, 'Pass'는 메소드 매개변수(들)을 바라본 관점인 것 같습니다.<br/>
* <strong>`Pass by Value` = `Call by Value`</strong>
<br/>
* <strong>`Pass by Reference` = `Call by Reference`</strong>
<br/>
<br/>

## Pass by Value (= Call by Value)
함수 호출시 매개변수로 전달한 인자의 메모리에 저장된 값(=value)을 복사해서 함수 내 매개변수로 사용하는 것<br>
* ★ 전달된 값을 복사해서 함수 내부에서 사용한 것이므로 값을 변형해도 전달한 함수 외부 변수 영향 無
* C 'Call by Value' Example
{% highlight c %}
void swap(int a, int b);

int main() {

   int ten = 10;
   int twenty = 20;

   swap(ten, twenty);

   // [Comment] Not Changed ten and twenty here 
   printf("ten = %d", ten); // 10
   printf("twenty = %d", twenty); // 20
}

void swap(int a, int b) {
 int temp = a;
 a = b;
 b = temp;
 // [Comment] Changed a and b here 
}
{% endhighlight %}
<br/>
<br/>

## Pass by Reference (= Call by Reference)
함수 호출시 매개변수로 전달한 인자의 메모리의 참조값(=주소값을) 전달해서 함수 내 매개변수로 사용하는 것</br>
* ★ 전달된 값을 복사해서 함수 내부에서 사용한 것이므로 값을 변형하면 전달한 함수 외부 변수에도 영향 有
* C 'Call by Reference' Example
{% highlight c %}
void swap(int *a, int *b);

int main() {

   int ten = 10;
   int twenty = 20;

   swap(&ten, &twenty);

   // [Comment] Changed ten and twenty here 
   printf("ten = %d", ten); // 20
   printf("twenty = %d", twenty); // 10
}

void swap(int *a, int *b) {
 int temp = *a;
 *a = *b;
 *b = *temp;
 // [Comment] Changed a and b here 
}
{% endhighlight %}
<br/>
<br/>

## 왜 Java는 Pass by Value (= Call by Value)인가?
<p>&nbsp;- 자바의 기본형(원시형) 변수(Primitive Type Variables)는 함수 매개변수 전달로 전달해도 외부에 영향을 주지 않는다.</p>
<p>&nbsp;&nbsp;의심할 여지없이 <strong>call by value</strong>이다.</p>
* Java Primitive type 'Call by Value' Example
 {% highlight java %}
 private static void plus10Toint(int a) {
    a+=10;
    // [Comment] Changed a of value here
 }
 
 public static void main(String[] args) {
     int primitVar = 10;
     System.out.println("primitVar = " + primitVar); // 10
     plus10Toint(primitVar);
     System.out.println("primitVar = " + primitVar); // 10
     
     // [Comment] Not Changed primitVar as 'Call by Value'
 }
 {% endhighlight %}
<br/>
<br/>

이제 헷갈리는 자바의 참조형 변수(Reference Type Variables)를 봐야한다.<br/>
<p>&nbsp;- 자바의 참조형 변수(Reference Type Variables)는 함수 매개변수 전달로 전달하면 외부에 영향을 준다. <br/>
마치 'Call by Reference'같다?!!;;;;</p>
* Java Reference type 'Call by Value' Example 1
 {% highlight java %}
 static class ObjClassVar {
     int propertyIntVar;
     ObjClassVar(int val) {
         this.propertyIntVar = val;
         // [Comment] Changed propertyIntVar of value here
     }
 }
 
 public static void main(String[] args) {
      ObjClassVar objClassVal = new ObjClassVar(10);
      System.out.println("propertyIntVar = " + objClassVal.propertyIntVar); // 10
      plus10ToObject(objClassVal);
      System.out.println("propertyIntVar = " + objClassVal.propertyIntVar); // 20
      
      // [Comment] Changed objClassVal.propertyIntVar like 'Call by Reference' Why?!!
 }
 
 private static void plus10ToObject(ObjClassVar argsObjClassVal) {
     argsObjClassVal.propertyIntVar += 10;
 }
 {% endhighlight %}
<p>&nbsp;&nbsp;하지만 그래도 <strong>call by value</strong>이다. 왜??</p>
Java는 앞서 언급한 듯이 **참조형 변수(Reference Type Variables)** 타입의 변수들이 있다.<br/>
그리고 `참조형 변수는 메모리에 저장된 값(=value)이 참조값(=주소값)`이다.<br/><br/>

그래서 이 참조형 변수들을 함수 호출시 매개변수로 전달하면 `Call by Value`인 자바는 </br>
참조형 변수의 메모리에 저장된 값(=value)인 참조값(=주소)를 복사하여 함수 내 매개변수로 준다.</br>
-> 위 예제에서는 plus10ToObject() 메소드를 호출할때 'objClassVal'의 값(=value)인 참조값(=주소)을 복사하여<br/>
plus10ToObject() 메소드 내 파라미터 'argsObjClassVal'의 값(=value)으로 전달하였다. **Call by Value**로써!<br/>
objClassVal와 argsObjClassVal의 변수 자체의 메모리의 참조값(=주소)는 다르지만, <br/>
메모리에 저장된 값(=value)인 참조값은 같은 ObjClassVar객체를 가리킨다.<br/>
 * 더불어 위는 이론이고 결과적 현상만 보면 Java는 `Call by Reference`와 같다. `Call by Value`인 증거는 뭐냐??하면<br/>
   보통 아래 예제처럼 함수에서 매개변수에 새로운 객체를 할당했음에도 함수 외부 객체는 영향을 받지 않음으로 `Call by Value`임을 확인시켜준다.<br/>
 * Java Reference type 'Call by Value' Example 2
{% highlight java %}  
 public static void main(String[] args) {
      ObjClassVar objClassVal = new ObjClassVar(10);
      System.out.println("propertyIntVar = " + objClassVal.propertyIntVar); // 10
      plus10ToObject(objClassVal);
      System.out.println("propertyIntVar = " + objClassVal.propertyIntVar); // 10
      
      // [Comment] Not Changed objClassVal.propertyIntVar as 'Call by Value'
 }
 
 private static void change20ToObject(ObjClassVar argsObjClassVal) {
     argsObjClassVal = new ObjClassVar(20);
 }
 {% endhighlight %}
 
 * 헷갈릴 것 같은 경우 [여기](https://stackoverflow.com/a/12429953) 그림으로 잘 설명해놓은 분이 있어 첨부한다. 
<br/>
<br/>
<br/>
음 이제 끝날 것 같지만 여기서 또 헷갈리는 녀석이 등장한다.<br/>
바로 Wrapper Class이다.<br/>
### Wrapper class ?
 : Java의 Primitive type variables를 객체로 사용해야하는 경우를 위해 포장한(=wrapper) 클래스.<br/>
 * Example
 int형의 Wrapper class  : `Integer`
 char형의 Wrapper class : `Character`
 boolean형의 Wrapper class : `Boolean`
 등등이 있다.
<br/>

<p>&nbsp;- Java의 래퍼형 클래스(Wrapper Class)는 Object로 참조형 변수 타입이지만, 함수 매개변수 전달로 전달하면 외부에 영향을 안준다. <br/>
   다른 참조형 변수들은 외부에 영향을 줘서 헷갈렸는데 얘는 참조형 변수인데 왜 안주는 것인가?</p>
 * Java Reference type 'Call by Value' Example 3
{% highlight java %}  
 public static void main(String[] args) {
      Integer refVar = 10;
      System.out.println("refVar = " + refVar); // 10
      plus10ToInteger(refVar);
      System.out.println("refVar = " + refVar); // 10
      
      // [Comment] Not Changed refVar as 'Call by Value'
 }
 
 private static void plus10ToInteger(Integer a) {
        a+=10;
 }
 {% endhighlight %}
 <br/>
<p>&nbsp;- 이 경우 plus10ToInteger()에서 unboxing & boxing 과정이 일어나서 그렇다.<br/>
a+=10; 을 수행할때에는 <br/>
ⓐ  a값을 unboxing하여 int value를 얻는다.<br/>
ⓑ  얻은 int값에 10을 더한다.<br/>
ⓒ  새 Integer Wrapper 객체에 10을 더한 int 값을 boxing한다.<br/>
 -> 이 과정은 마치 Example2와 같다. </br>
 매개변수는 Call by Value로 전달되었으나, 함수 내부에서 새로운 Integer 객체를 참조하도록 값이 변경되었으므로 함수 외부에는 영향을 주지 않는 것이다.
</p>
<br/>
<br/>
<br/>
## Refs

* [Stackoverflow, Are call-by-value and pass-by-value synonymous?](https://stackoverflow.com/a/4987266)
* [Stackoverflow, Is Java “pass-by-reference” or “pass-by-value”?](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value)
* [Stackoverflow, pass array by reference in java] (https://stackoverflow.com/questions/14062118/pass-array-by-reference-in-java)
* [자바의 아규먼트 전달 방식] (https://brunch.co.kr/@kd4/2)
* [래퍼 클래스(wrapper class)] (https://jusungpark.tistory.com/17)
* [[JAVA] Wrapper class 란? 그리고 AutoBoxing] (https://hyeonstorage.tistory.com/168)
* [C언어 값에 의한 호출 (Call by Value), 참조에 의한 호출 (Call by Reference)] (https://goandroidtips.com/blog/c%EC%96%B8%EC%96%B4-%EA%B0%92%EC%97%90-%EC%9D%98%ED%95%9C-%ED%98%B8%EC%B6%9C-%EC%B0%B8%EC%A1%B0%EC%97%90-%EC%9D%98%ED%95%9C-%ED%98%B8%EC%B6%9C/)
* [Wrapper classes and call by reference in java [duplicate]] (https://stackoverflow.com/a/20804991)
* [Call By Reference와 Call By Value] (https://okky.kr/article/303162?note=1005863)
