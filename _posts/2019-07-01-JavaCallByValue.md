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
