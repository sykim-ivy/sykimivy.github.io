---
layout: post
title: 코틀린 주요 특징
category: Kotlin
tags: [Kotlin]
---

쓰다보면 자연스럽게 익숙해지지만 안쓰면 또 까먹는 코틀린의 주요 특징을 정리해보자! 

# 코틀린 주요 특징 (Kotlin Feature)

기존 안드로이드 개발 공식 언어는 Java였으나,  
Google I/O 2017 에서 안드로이드 공식 언어로 'Kotlin'으로 채택되었다.  

저 당시에는 내가 웹개발자여서 그냥 넘어갔었는데 안드로이드 개발을 하면서 생각해보니  
내가 살면서 공식 개발 언어가 바뀐 적은 처음이다!  

그래서 신기하기도 하고 또 약간의 배움의 부담도 느껴지고 그런데 또 궁금하기도 하고하니  
시작하자 코틀린!!  
 &nbsp;
 &nbsp;
 &nbsp;
## 코드 작성시 
### 1. 코드 문장 끝에 ';'을 찍지 않는다
* `Java` Code Example
<figure class="highlight"><pre>
<code class="language-tex" data-lang="tex">  private val titleStr: String = "Hello World, I'm Title!"<span style="color:red;background-color: yellow;">;</span></code>
</pre></figure>
  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="n">val</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>  
 &nbsp;
 &nbsp;
 &nbsp;

## 접근제한자 선언시
### 접근제한자 생략시 'public'으로 설정된다
  
&nbsp;- 여긴 함수 선언시도 동일하다!
  
| 접근제한자 | 접근 가능 범위 |
|:---:|----|
| **public** | 어디서든 접근 가능 (<span style="color:red;"><strong>디폴트</strong></span>) |
| **internal** | <strong><u>동일 모듈</u></strong> 내에서 접근 가능 |
| protected | 선언된 클래스를 상속받은 클래스에서 접근 가능 |
| privated | 선언된 클래스 내에서만 접근 가능 |
  
 &nbsp;
 &nbsp;
 &nbsp;

## 타입 선언시
### 모든 타입은 Nullable 여부를 명시해야 한다
&nbsp;- 코틀린(kotlin)은 null값 허용여부를 컴파일 단게에서 수행한다.

##### &nbsp;&nbsp;&nbsp;-  Null값 비허용 타입(Non-Null) :  <strong>`타입명`</strong>  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr:</span> <span class="s"> String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>

##### &nbsp;&nbsp;&nbsp;-  Null값 허용 타입(Nullable) : <strong>`타입명?`</strong>  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr:</span> <span class="s"> String</span><span style="color:red;background-color: yellow;">?</span><span class="o">=</span> <span class="">null</span></code></pre></figure>
&nbsp;※ 변수선언시 타입을 생략하는 경우, null을 허용하지 않는 타입으로 지정된다
  
  
 &nbsp;
 &nbsp;
 &nbsp; 

## 변수 선언시 
### 1. 맨앞에 타입 가변성을 명시한다

##### &nbsp;&nbsp;&nbsp;-  값이 변하지 않는 변수일 경우 <strong>`val`</strong>  
##### &nbsp;&nbsp;&nbsp;-  값이 변할 수 있는 변수일 경우 <strong>`var`</strong><span style="font-size: 12px;color: gray;">(<< Java의 'final' 키워드 같은)</span>  

<p>&nbsp;-<code class="highlighter-rouge">val</code>은 value, <code class="highlighter-rouge">var</code>는 variable의 약자로 추정된다.&nbsp;<span style="font-size: 12px;color: gray;">(‘var’는 javascript 같아서 반갑네 ㅎㅎ)</span></p>
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="s">val</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>  
&nbsp; 
&nbsp; 

### 2. 변수타입은 '변수명: 변수타입'으로 적거나 생략도 가능하다
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr</span> <span class="s">: String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>
&nbsp;- 변수타입 생략시 변수에 대입되는 값을 바탕으로 타입을 추론한다. <span style="font-size: 12px;color: gray;">(이때 타입은 non-null타입임을 명심하자!)</span>
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>  
&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 


## Refs

* [Imooc 十天精通CSS3](http://www.imooc.com/learn/33)
* [CSS Animation for Beginners](https://robots.thoughtbot.com/css-animation-for-beginners#animation-iteration-count)
* [CSS3 animation-timing-function Property](http://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp)
