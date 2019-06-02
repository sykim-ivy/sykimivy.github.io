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

## 변수 선언시 
### 1. 맨앞에 타입 가변성을 명시한다

##### &nbsp;&nbsp;&nbsp;-  값이 변하지 않는 변수일 경우 <strong>`val`</strong>  
##### &nbsp;&nbsp;&nbsp;-  값이 변할 수 있는 변수일 경우 <strong>`var`</strong><span style="font-size: 13px;color: gray;">  (<< Java의 'final' 키워드 같은)</span>  

<p>&nbsp;-<code class="highlighter-rouge">val</code>은 value, <code class="highlighter-rouge">var</code>는 variable의 약자로 추정된다.&nbsp;<span style="font-size: 12px;color: gray;"> (‘var’는 javascript 같아서 반갑네 ㅎㅎ)</span></p>
* `Kotlin` Code Example
<!--val 예시-->
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="s">val</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"
<br/>   titleStr = "Try change the value"</span>     <span style="color:red;background-color: yellow;">Error : 빨간줄 발생 'Val cannot be reassigned'</span>
</code></pre></figure>  
<!--var 예시-->
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="s">var</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"
<br/>   titleStr = "Try change the value"</span>     <span style="color:blue;background-color: yellow;">Not Error : 'var'변수는 언제든 값 변경 가능</span>
</code></pre></figure>  
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

## 메소드(함수,function) 선언시 
### 1. 함수 선언시 아래 순서를 따른다.

`fun 함수명(파라미터명: 파라미터타입, ...): 리턴타입 { 함수 실행문 }`

&nbsp;- 리턴값이 없는 경우 생략가능하고 리턴값이 없는 것을 명시할 경우 'Unit'으로 쓸 수 있다.
<br/>
&nbsp;&nbsp;&nbsp;<span style="font-size: 14px;color: #6f3016;">cf) Java의 경우도 리턴값이 없는 경우 생략가능하고, 명시할 경우 'void'로 쓸 수 있다.</span>

<br/>

### 2. override 함수는 선언시 맨 앞에 `override`키워드로 명시한다
<br/>
 &nbsp;
* `Kotlin` Code Example
{% highlight java %}
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.main_activity_layout)
    }
{% endhighlight %}
* `Java` Code Example
{% highlight java %}@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main_activity_layout)
    }
{% endhighlight %}
&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 

## 객체 생성시 
### 객체 생성시 'new'를 쓰지 않는다
&nbsp;- Kotlin의 최상위 객체는 'Any'클래스이다.

&nbsp;&nbsp;&nbsp;<span style="font-size: 14px;color: #6f3016;">cf) Java의 경우 'Object'클래스이다.</span>
* `Java` Code Example
<figure class="highlight"><pre>
<code class="language-tex" data-lang="tex">  private Object tempObj = <span style="color:red;background-color: yellow;">new</span> Object();</code>
</pre></figure>
  
* `Kotlin` Code Example
<figure class="highlight"><pre>
<code class="language-tex" data-lang="tex">  private val tempObj = Any()</code>
</pre></figure>
   

&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 
## 객체 생성시 
### 객

&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 
## 기타 외 특징들
### 람다 표현식(Lamda)을 지원한다
### 스트림 API(Stream API)를 지원한다
&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 
&nbsp;- Kotlin의 최상위 객체는 'Any'클래스이다.


## Refs

* [Imooc 十天精通CSS3](http://www.imooc.com/learn/33)
* [CSS Animation for Beginners](https://robots.thoughtbot.com/css-animation-for-beginners#animation-iteration-count)
* [CSS3 animation-timing-function Property](http://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp)
