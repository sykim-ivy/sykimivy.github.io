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
 <p style="color: #c7254e;">N개 중 S개를 뽑아 <strong>순서대로</strong> 나열하는 경우의 수</p>
  * Example <br>
    빨주노초파남보 7가지 색 중에 3가지를 뽑아 나열하는 경우의 수 => <sub>7</sub>P<sub>3</sub>
<br>
<br>
 * 공식<br>
<sub>N</sub>P<sub>S</sub> = N * (N-1) * ... * ( N-(S-1) )
 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= N부터 1개씩 작아지는 수들을 총 S개를 곱함
<br>
<br>
 * Example value <br>
    <sub>7</sub>P<sub>3</sub> = 7 * 6 * 5 = 210
    <br>
    <br>
 * `팩토리얼`  = <sub>N</sub>P<sub>N</sub> : N개를 순서대로 나열하는 경우의 수<br>
    <sub>N</sub>C<sub>N</sub>  =  N * (N-1) * ... * 1 = `N!`
<br>
<br>
<br> 


<h2>조합 <sub>N</sub>C<sub>S</sub> </h2>
 <p style="color: #c7254e;"><strong>순서없이</strong> N개 중 S개를 뽑은 경우의 수</p>
  * Example <br>
    빨주노초파남보 7가지 색 중에 3가지를 뽑는 경우의 수 => <sub>7</sub>C<sub>3</sub>
<br>
<br>
 * 공식<br>
<sub>N</sub>C<sub>S</sub> = <sup>N * (N-1) * ... * ( N-(S-1) )</sup> / <sub>S * (S-1) * ... * 1</sub> 
 <br><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= <sup>N부터 1개씩 작아지는 수들을 총 S개를 곱함</sup>  /  <sub>S부터 1개씩 작아지는 수 총 S개를 곱함 (=S!)</sub>
<br>
<br>
 * Example value <br>
    <sub>7</sub>C<sub>3</sub> = <sup>7 * 6 * 5</sup>  /  <sub>3 * 2 * 1</sub> = 35
    <br>
    <br>
 * 추가적으로 다음과 같은 공식도 성립한다.<br>
    <sub>N</sub>C<sub>S</sub> = <sub>N</sub>C<sub> (N - S)</sub> <br>
 <br>
 * 어쩌면 당연한 공식<br>   
    <sub>N</sub>C<sub>(N - 1)</sub> = N
 <br>
 N개에서 S개를 순서없이 뽑으면 남은 (N-S)개들도 일종의 조합이 된다.<br> 
 그러므로 N개에서 (N-S)개를 순서없이 뽑는 값과 같다.<br>
 <br/>* 이 외에 조합에는 [파스칼의 삼각형 공식](http://blog.naver.com/PostView.nhn?blogId=baboedition&logNo=220929686431)들이 있는데 생략한다.<br>
<br> 
<br/> 
<br/> 
당연한 말이지만 순서대로 나열한 순열이 항상 조합보다 클 수 밖에 없다.<br>
순열에서는 (빨,주,노) != (노,빨,주) 부터 다르니까 <br>
<br/> 
<br/> 

## N개의 입력값 중 최댓값을 찾을때 입력값들의 경우의 수
<br/>
최대값을 찾아야하므로 모든 값은 대소를 비교할 수 밖에 없다.<br>
즉, 모든 수들의 대소가 순위처럼 결정된다고 보면 우위가 생기며, 동일한 값은 서로 우위가 없으므로 하나로 본다.<br/>
그렇다면 경우의 수는 다음과 같다.<br/>

<br/>
### 1. N개의 입력값이 모두 다르며 N개 우위가 있는 경우의 수
이 경우는 간단하다. 총 
<p style="color:#2098d1">N!</p>
가지 경우이다.<br/>
위의 팩토리얼 정의와 같이 N개를 순서대로 나열하는 경우의 수이기때문이다. <br>
<br/>
<br/>
### 2. N개 중 일부 입력값이 같은 경우
#### 2-1. (N-1)개가 같은 값이고 1개의 수가 다른 경우
 ⓐ 우선,  N개중 같은 값을 가질 (N-1)개를 뽑을 확률 =>  <sub>N</sub>C<sub>(N - 1)</sub> = <b>N</b><br>
 ⓑ (N-1)과 남은 1개, 총 2가지 값이 우위를 가지는 경우의 수 = 2개를 순서대로 나열하는 경우의 수 => <b>2!</b><br><br>
총 
<p style="color:#2098d1">N * 2!</p>
 가지 경우
<br>
<br>
#### 2-2. (N-2)개가 같은 값이고 2개의 수가 다른 경우
 ⓐ 우선,  N개중 같은 값을 가질 (N-2)개를 뽑을 확률 =>  <sub>N</sub>C<sub>(N - 2)</sub>
 ⓑ (N-2)과 남은 2개, 총 3가지 값이 우위를 가지는 경우의 수 = 3개를 순서대로 나열하는 경우의 수 => <b>3!</b><br><br>
총 
<p style="color:#2098d1"><sub>N</sub>C<sub>(N - 2)</sub> * 3!</p>
 가지 경우
<br>
<br>
<br>
#### 2-3. (N-3)개가 같은 값이고 3개의 수가 다른 경우
 ⓐ 우선,  N개중 같은 값을 가질 (N-3)개를 뽑을 확률 =>  <sub>N</sub>C<sub>(N - 3)</sub>
 ⓑ (N-2)과 남은 3개, 총 4가지 값이 우위를 가지는 경우의 수 = 3개를 순서대로 나열하는 경우의 수 => <b>4!</b><br><br>
총 
<p style="color:#2098d1"><sub>N</sub>C<sub>(N - 2)</sub> * 3!</p>
 가지 경우
<br>
<br>
<br>
이런 식으로 반복하다보면, 마지막으로는 1번의 경우와 같아지므로 이 경우는 제외한다.<br>
#### 2-N. (N-N) = 0개가 같은 값이고 N개의 수가 다른 경우 = 즉, N개의 입력값이 모두 다르며 N개 우위가 있는 경우의 수
<br>
<br>
<br>
### 3. N개의 입력값이 모두 같은 경우의 수
이 경우는 간단하다. N개에서 N개를 모두 뽑는 조합 <sub>N</sub>C<sub>N</sub>으로 <br>
총 
<p style="color:#2098d1">1</p>
 가지 경우이다.<br/>









<br/><br/><br/>


## Refs

* [보요 시바타, Do it! 자료구조와 함께 배우는 알고리즘 입문, 강민,  이지스퍼블리싱(2018)](https://book.naver.com/bookdb/book_detail.nhn?bid=13560672)
* [잘 설명해주신 순열과 조합](http://blog.naver.com/PostView.nhn?blogId=baboedition&logNo=220929686431)

