---
layout: post
title: 알고리즘 공부를 위한 기초 기초 개념(순차,선택 구조/ 자바 입력받기 / 
category: Algorithm-Basic
tags: [Algorithm-Basic]
---
<br><br>
'Do it! 자료구조와 함께 배우는 알고리즘 입문' 책을 참고하였다.
알고리즘 공부 전 알아야할 기초 중에 기초 개념이라 검색하면 정보도 많다.
<br><br>
## 프로그래밍 문장 실행 구조

### Concatenation(순차적) 구조 : 여러 문장이 첫문장부터 순서대로 실행되는 구조
### Selection(선택) 구조 : 조건에 따라 조건에 맞는 문장이 실행되는 구조
<br><br>

## Java 값 입력 받기
키보드와 연결된 입력 스트림 System.in으로부터 입력받은 값을 가져오는 장치 역할이라고 한다.
{% highlight java %}
   Scanner stdIn = new Scanner(System.in);
   int v1 = stdIn.nextInt(); // 정수값 입력받음 원하는 입력 타입에 맞는 함수를 사용하면 된다.
{% endhighlight %} 

<br>

<br/><br/><br/>


## Refs

* [보요 시바타, Do it! 자료구조와 함께 배우는 알고리즘 입문, 강민,  이지스퍼블리싱(2018)](https://book.naver.com/bookdb/book_detail.nhn?bid=13560672)
