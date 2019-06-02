---
layout: post
title: 코틀린 주요 특징1 (코드, 접근제한자, 타입 관련)
category: Kotlin
tags: [Kotlin]
---

쓰다보면 자연스럽게 익숙해지지만 안쓰면 또 까먹는 코틀린의 주요 특징을 정리해보자! 

# 코틀린 주요 특징 1 (Kotlin Feature)

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
### 문장 끝에 ';'을 찍지 않는다
* `Java` Code Example
<figure class="highlight"><pre>
<code class="language-tex" data-lang="tex">  private String titleStr = "Hello World, I'm Title!"<span style="color:red;background-color: yellow;">;</span></code>
</pre></figure>
  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="n">val</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>  
 &nbsp;
 &nbsp;
 &nbsp;

## 접근제한자 선언시
### 접근제한자 생략시 'public'으로 설정된다
  
&nbsp;※ 명시하지 않는 경우 디폴트 접근제한자 `public`으로 지정되니 주의!!
  
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
### 1.모든 타입은 Nullable 여부를 명시해야 한다
&nbsp;- 코틀린(kotlin)은 null값 허용 여부 검사를 컴파일 단게에서 수행한다.

##### &nbsp;&nbsp;&nbsp;-  Null값 비허용 타입 (Non-Null) :  <strong>`타입명`</strong>  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr:</span> <span class="s"> String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>

##### &nbsp;&nbsp;&nbsp;-  Null값 허용 타입 (Nullable) : <strong>`타입명?`</strong>  
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr:</span> <span class="s"> String</span><span style="color:red;background-color: yellow;">?</span><span class="o">=</span> <span class="">null</span></code></pre></figure>
&nbsp;※ 변수선언시 타입을 생략하는 경우, null을 허용하지 않는 타입으로 지정된다
 &nbsp; 
 &nbsp;   
<br/><br/>

### 2.컬렉션 타입은 '컬렉션 내 자료 가변 여부'에 따라 나뉜다

##### &nbsp;&nbsp;&nbsp;-  자료값이 변하는 경우 <strong>`Mutable 타입`</strong>  
&nbsp;- 자료값의 추가/읽기/변경/삭제 (=CRUD) 모두 가능!
* `Kotlin` Code Example
{% highlight java %}
   var dessertBasket: MutableList<String> = mutableListOf("Nougat", "Oreo", "Pie")
   dessertBasket.add("Quesito") // [추가]
   dessertBasket[2] // [읽기] : Same this code >> 'dessertBasket.get(2)'
   dessertBasket[2] = "Oreo Mint flavor!" // [변경] : Same this code >> 'dessertBasket.set(2, "Oreo Mint flavor!")'
   dessertBasket.removeAt(0) // [삭제] Delete element at index 0, value("Nougat")
{% endhighlight %} 

##### &nbsp;&nbsp;&nbsp;-  자료값이 변하지 않는 경우 <strong>`Immutable 타입`</strong>  
&nbsp;- 자료값의 읽기만 (= Read only) 가능! 변경 불가능!!
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-java" data-lang="java">   <span class="n">val</span> <span class="nl">dessertBasket:</span> <span class="n">List</span><span class="o">&lt;</span><span class="n">String</span><span class="o">&gt;</span> <span class="o">=</span> <span class="n">listOf</span><span class="o">(</span><span class="s">"Nougat"</span><span class="o">,</span> <span class="s">"Oreo"</span><span class="o">,</span> <span class="s">"Pie"</span><span class="o">)</span>
   <span class="n">dessertBasket</span><span class="o">.</span><span class="na">add</span><span class="o">(</span><span class="s">"Quesito"</span><span class="o">)</span>     <span style="color:red;background-color: yellow;float: right;">Error : 빨간줄 발생 'unresolved reference'</span>
<span class="n">    dessertBasket</span><span class="o">[</span><span class="mi">2</span><span class="o">]</span>
   <span class="n">dessertBasket</span><span class="o">[</span><span class="mi">2</span><span class="o">]</span> <span class="o">=</span> <span class="s">"Oreo Mint flavor!"     <span style="color:red;background-color: yellow;float: right;">Error : 빨간줄 발생 'unresolved reference'</span></span>
   <span class="n">dessertBasket</span><span class="o">.</span><span class="na">removeAt</span><span class="o">(</span><span class="mi">0</span><span class="o">)</span><span style="color:red;background-color: yellow;float: right;">Error : 빨간줄 발생 'unresolved reference'</span></code></pre></figure>

&nbsp;- Kotlin은 기존 Java 컬렉션 클래스들을 타입 별칭(type alias)로 사용한다.
<br/><br/>
&nbsp;- 관련된 별도의 포스팅 첨부 예정
<br/><br/><br/>

&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 


## Refs

* [Imooc 十天精通CSS3](http://www.imooc.com/learn/33)
* [CSS Animation for Beginners](https://robots.thoughtbot.com/css-animation-for-beginners#animation-iteration-count)
* [CSS3 animation-timing-function Property](http://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp)
