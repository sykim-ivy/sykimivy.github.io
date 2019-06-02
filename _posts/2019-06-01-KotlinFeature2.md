---
layout: post
title: 코틀린 주요 특징2 (변수, 메소드, 객체 관련)
category: Kotlin
tags: [Kotlin]
---

# 코틀린 주요 특징 2 (Kotlin Feature)

이 포스트에 정리되는 코틀린의 특징은 극히 일부분이다. &nbsp;
'코틀린 주요 특징 1,2,3' 포스트에 정리된 내용 외에도 클래스, 상속 등등등 코틀린의 특징은 무수히 많다. &nbsp;

그 중 코드 작성시 매번 마주치는 부분만 뽑아 정리해놓으려 한다. &nbsp;
 &nbsp;

## 변수 선언시 
### 1. 맨앞에 타입 가변성을 명시한다
<p>&nbsp;-<code class="highlighter-rouge">val</code>은 value, <code class="highlighter-rouge">var</code>는 variable의 약자로 추정된다.&nbsp;<span style="font-size: 12px;color: gray;"> (‘var’는 javascript 같아서 반갑네 ㅎㅎ)</span></p>
<br/>  

##### &nbsp;&nbsp;&nbsp;-  값이 변하지 않는 변수일 경우 <strong>`val`</strong>  
* `Kotlin` Code Example
<!--val 예시-->
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="s">val</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"
<br/>   titleStr = "Try change the value"</span>     <span style="color:red;background-color: yellow;">Error : 빨간줄 발생 'Val cannot be reassigned'</span>
</code></pre></figure>  

<br/>  

##### &nbsp;&nbsp;&nbsp;-  값이 변할 수 있는 변수일 경우 <strong>`var`</strong><span style="font-size: 13px;color: gray;">  (<< Java의 'final' 키워드 같은)</span>
* `Kotlin` Code Example
<!--var 예시-->
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="s">var</span> <span class="">titleStr:</span> <span class="n">String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"
<br/>   titleStr = "Try change the value"</span>     <span style="color:blue;background-color: yellow;">Not Error : 'var'변수는 언제든 값 변경 가능</span>
</code></pre></figure>  
 &nbsp;
 &nbsp;

### 2. 변수타입은 '변수명: 변수타입'으로 적거나 생략도 가능하다
* `Kotlin` Code Example
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr</span> <span class="s">: String</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>
<br/>  
&nbsp;- 변수타입 생략시 변수에 대입되는 값을 바탕으로 타입을 추론한다. <span style="font-size: 12px;color: gray;">(이때 타입은 non-null타입임을 명심하자!)</span>
<figure class="highlight"><pre><code class="language-tex" data-lang="tex"><span class="">   private</span> <span class="">val</span> <span class="">titleStr</span> <span class="o">=</span> <span class="">"Hello World, I'm Title!"</span></code></pre></figure>  
&nbsp; 
&nbsp; 
&nbsp; 
&nbsp; 

## 메소드(함수,function) 선언시 
### 1. 함수 선언시 아래 순서를 따른다.

<figure class="highlight"><pre><code class="language-java" data-lang="java" style="
    font-size: 22px;
"> <span class="nd">fun</span> <span class="nf">함수명</span><span class="o">(</span><span class="s">파라미터명</span><span class="o">:</span> <span class="s">파라미터타입</span><span class="o">,</span> <span class="o">...):</span> <span class="kt">리턴타입</span> <span class="o">{</span> 
                <span class="">~</span> <span class="">함수</span> <span class="">실행문</span> <span class="">~</span> 
  <span class="o">}</span></code></pre></figure>

&nbsp;- 리턴값이 없는 경우 생략가능하고 리턴값이 없는 것을 명시할 경우 'Unit'으로 쓸 수 있다.
<br/>
&nbsp;&nbsp;&nbsp;<span style="font-size: 14px;color: #6f3016;">cf) Java의 경우도 리턴값이 없는 경우 생략가능하고, 명시할 경우 'void'로 쓸 수 있다.</span>
<br/><br/>
### 2. override 함수는 선언시 맨 앞에 `override`키워드로 명시한다
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

&nbsp;&nbsp;&nbsp;<span style="font-size: 14px;color: #6f3016;">cf) Java의 경우 최상위 객체는 'Object'클래스이다.</span>
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

## Refs

* [Imooc 十天精通CSS3](http://www.imooc.com/learn/33)
* [CSS Animation for Beginners](https://robots.thoughtbot.com/css-animation-for-beginners#animation-iteration-count)
* [CSS3 animation-timing-function Property](http://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp)

