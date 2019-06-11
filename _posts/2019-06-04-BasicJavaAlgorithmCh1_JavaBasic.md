---
layout: post
title: 자바 알고리즘 입문 ch1 (자바 입력받기, 알고리즘이란?)
category: Algorithm-Basic
tags: [Algorithm-Basic]
---

<br>

## Java 값 입력 받기
키보드와 연결된 입력 스트림 System.in으로부터 입력받은 값을 가져오는 장치 역할이라고 한다.
{% highlight java %}
   Scanner stdIn = new Scanner(System.in);
   int v1 = stdIn.nextInt(); // 정수값 입력받음 원하는 입력 타입에 맞는 함수를 사용하면 된다.
{% endhighlight %} 

<br>
## 알고리즘?
책의 개념은 너무 어렵다. <br/>
맞는지 모르겠지만 내가 이해한 개념은 아래와 같다. 
`문제를 해결하기 위한 일렬의 논리구조(명확하고 규칙으로 이루어져 있는)`


<br/><br/><br/>

## Refs

* [보요 시바타, Do it! 자료구조와 함께 배우는 알고리즘 입문, 강민,  이지스퍼블리싱(2018)](https://book.naver.com/bookdb/book_detail.nhn?bid=13560672)
