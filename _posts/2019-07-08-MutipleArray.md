---
layout: post
title: Java - 다차원 배열(Multiple Array)
category: Java
tags: [Java]
---

## 배열은 참조형 변수
자바에서 배열을 값으로 가지는 변수는 `참조형 변수(Reference Type Variables)`이다.<br/>
* Example)
~~~java
int[] a = new int[4]; // 선언
int[] b = {1, 2, 3, 4} // 선언 및 초기화
~~~
그러므로 위의 변수 'a', 'b'는 <strong>정수형 배열</strong>을 가리키는 참조값(=일종의 주소값)을 가진다.<br/>
그리고 이 <strong>정수형 배열</strong>은 int[]형이고, 구성요소수(=a.length) 4이다.<br/>
&nbsp;- 비어있는 배열(length=0)인 배열도 선언 가능하다.<br/>
<br/>
<br/>
## IndexOutOfException
 * <strong>배열의 접근은 모두 Runtime시에 검사된다!</strong>
 * 접근할 수 없는 배열 요소(0미만 또는 배열 요솟수 이상의 인덱스)에 접급한 경우 발생하는 익셉션
 * Example)
~~~java
int[] a = new int[2]; // 선언
a[2]; // IndexOutOfException
~~~
<br/>
<br/>
## 다차원 배열
: 배열의 구성요소로 배열을 가진 배열 (배열값이 배열)<br/>
&nbsp;- 1차원이 아닌 2차원 이상의 모든 배열<br/>

* 2차원 배열 Example)
{% highlight java %}
int[][] x = new int[2][3]; // 2차원 배열
int[][][] x1 = new int[2][3][4]; // 3차원 배열

x[1][2] = 3;
{% endhighlight %}

<br/>

* 위 2차원 배열 Example은 아래 코드를 줄인 것이다.

{% highlight java %}
int[][] x;
x = new int[2][];
x[0] = new int[3];
x[1] = new int[3];

x[1][2] = 3; // 위 줄 '= new int[3]'배열의 2번째 인덱스에 값 3을 대입
{% endhighlight %}

&nbsp;- x[0]과 x[1]은 같은 사이즈가 아니여도 된다.<br/>
<br/>

* 2차원 배열 선언과 초기화

{% highlight java %}
int[][] y = { {1, 2, 3}, {4, 5, 6, 7}};
{% endhighlight %}

<br/>
<br/>
## 다차원 배열의 복제
다차원 배열을 clone()함수로 복제시 최상위 1레벨만 복제가 수행됩니다.<br/>
* Example
{% highlight java %}
int[][] y = { {1, 2, 3}, {4, 5, 6, 7}};
z = y.clone();
{% endhighlight %}

&nbsp;- y[0], y[1]은 복제되어 새로 메모리에 z[0], z[1]이 생성되지만,<br/>
&nbsp;- y[0], y[1]이 참조값으로 가리키는 배열은 메모리에 새로 생성되는 것이 아니고, </br>y[0], z[0]이 y[1], z[1] 가 같은 배열을 참조하게된다.<br/>
<br/>
<br/>

## Refs

* [보요 시바타, Do it! 자료구조와 함께 배우는 알고리즘 입문, 강민,  이지스퍼블리싱(2018)](https://book.naver.com/bookdb/book_detail.nhn?bid=13560672)
