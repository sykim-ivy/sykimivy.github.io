---
layout: post
title: Java is always 'Call by value' = 'Pass by Value'
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

