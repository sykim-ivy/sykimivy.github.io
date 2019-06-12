---
layout: post
title: N개의 값 중 최대값 or 최소값을 구하는 알고리즘 경우의 수
category: Algorithm-Basic-Github
tags: [Algorithm-Basic-Github]
---
<br><br>
N개의 입력값 중 최댓값을 구하는 알고리즘 코드를 작성하다가<br>
최대값 혹은 최소값이 발생할 수 있는 경우의 수가 궁금해졌다.<br>
<br>
<br>
찾다보니 이는 `순열`과 `조합`을 알아야한다.<br>
<br>
<h2> 순열 <sub>N</sub>P<sub>S</sub> </h2>
 : <p style="color: #c7254e;">N개 중 S개를 뽑아 <strong>순서대로</strong> 나열하는 경우의 수</p>  <br>
  * Example <br>
    빨주노초파남보 7가지 색 중에 3가지를 뽑아 나열하는 경우의 수 => <sub>7</sub>P<sub>3</sub>
<br>
<br>
 * 공식<br>
<sub>N</sub>P<sub>S</sub> = N * (N-1) * ... * ( N-(S-1) )
 <br>
&nbsp;&nbsp;&nbsp;&nbsp;= N부터 1개씩 작아지는 수들을 총 S개를 곱함
<br>
<br>
 * Example value <br>
    <sub>7</sub>P<sub>3</sub> = <sup>7 * 6 * 5</sup> = 210
    <br>
<br>
<br> 


<h2> 조합 <sub>N</sub>C<sub>S</sub> </h2>
 : <p style="color: #c7254e;"><strong>순서없이</strong> N개 중 S개를 뽑은 경우의 수</p><br>
  * Example <br>
    빨주노초파남보 7가지 색 중에 3가지를 뽑는 경우의 수 => <sub>7</sub>C<sub>3</sub>
<br>
<br>
 * 공식<br>
<sub>N</sub>C<sub>S</sub> = <sup>N * (N-1) * ... * ( N-(S-1) )</sup> / <sub>S * (S-1) * ... * 1</sub> 
 <br>
&nbsp;&nbsp;&nbsp;&nbsp;= <sup>N부터 1개씩 작아지는 수들을 총 S개를 곱함</sup>  /  <sub>S부터 1개씩 작아지는 수 총 S개를 곱함 (=S!)</sub>
<br>
<br>
 * Example value <br>
    <sub>7</sub>C<sub>3</sub> = <sup>7 * 6 * 5</sup>  /  <sub>3 * 2 * 1</sub> = 35
    <br>
<br>
<br> 



## N개의 입력값 중 최댓값을 구하는 알고리즘
<br/>
입력값의 수에 따라 몇가지의 경우의 수가 생기는지 궁금하다.<br/>
먼저 알고 있어야할 수학공식을 소개한다.<br/>
## N개 중에서 m개를 뽑는 순열의 수 공식
``
`N!/(N-m)!*m!`

<br/><br/><br/>
이제 본격적으로 계산을 시작해보자! <br/>
핵심 과제는 <strong>N개의 입력값 중 최댓값을 구하는 경우의 수</strong>
<br/>
### 1. N개의 입력값이 모두 달라서 우위가 있는 경우의 수
이 경우는 간단하다.<br/>
총 `N!`가지 경우이다.<br/>
<br/>

### 2. N개 중 일부 입력값이 같은 경우

#### 2-1. (N-1)개가 같은 값이고 1개의 수가 다른 경우
#### 2-1. (N-2)개가 같은 값이고 2개의 수가 다른 경우
#### 2-1. (N-3)개가 같은 값이고 2개의 수가 다른 경우









<br/><br/><br/>


## Refs

* [보요 시바타, Do it! 자료구조와 함께 배우는 알고리즘 입문, 강민,  이지스퍼블리싱(2018)](https://book.naver.com/bookdb/book_detail.nhn?bid=13560672)
