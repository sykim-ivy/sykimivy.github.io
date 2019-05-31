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

## 코드작성시 특징

### 1. 코드 문장 끝에 ';'을 찍지 않는다
 : 자바에서 ';'를 붙이던 모든 문장에 세미콜론을 붙이지 않는다

* `Java Code Example`
```
   private String titleStr = "Hello World, I'm Title!"<span style="color:red">;</
```
* `Kotlin Code Example`
{% highlight tex %}
   private val titleStr: String = "Hello World, I'm Title!"
{% endhighlight %}


* Name of the animation. For example, changeColor.
* Stages: From 0% to 100% to represent the whole process of animation
* CSS Properties: The CSS properties defined for each stage of the animation timeline.

Following example creates an animation called `changeColor` and assign it to `div:hover`:

{% highlight css %}
@keyframes changeColor {
  0% {
    background: red;
  }
  60% {
    background: blue;
  }
  100%{
    background: green;
  }
}

div:hover{
  animation: changeColor 5s ease .1s;
}
{% endhighlight %}

> In above example, we could also use `from` to represent `0%` and `to` to represent `100%`

## Animation Properties

It has following properties: 

1. animation-name
2. animation-duration
3. animation-timing-function
4. animation-delay
5. animation-iteration-count
6. animation-direction
7. animation-fill-mode
8. animation-play-state

### animation-name

The name of the animation, defined in the @keyframes.

### animation-duration

The duration of the animation, in seconds (e.g., 5s) or milliseconds (e.g., 200ms).

### animation-timing-function

The speed curve or pace of the animation:

| Timing Function | Description |
|---|---|
| linear | The animation has the same speed from start to end |
| ease | **Default value**. The animation has a slow start, then fast, before it ends slowly. |
| ease-in | Start slowly and end fast.  |
| ease-out | Start more quickly than linear ones and end slowly. The opposite of ease-in. |
| ease-in-out | Both a slow start and a slow end |
| initial | Sets this property to its default value. So `ease`. |
| inherit | Inherits this property from its parent element. |

> Check [The basics of easing](https://developers.google.com/web/fundamentals/design-and-ui/animations/the-basics-of-easing?hl=en) for details.

### animation-delay 

It specifies when the animation will start. The value is defined in seconds (s) or milliseconds (mil).

### animation-iteration-count

It specifies the number of times that the animation will play. The possible values are:

* a specific number of iterations (default is 1)
* `infinite` - repeats forever
* `initial`
* `inherit`

### animation-direction

It specifies whether the animation should play forward, reverse, or in alternate cycles.

* `normal` - Default. On each cycle the animation resets to the beginning state (0%) and plays forward again (to 100%).

* `reverse` - On each cycle the animation resets to the end state (100%) and plays backwards (to 0%).

* `alternate` - On each odd cycle, the animation plays forward (0% to 100%). On each even cycle, the animation plays backwards (100% to 0%).

* `alternate-reverse` - On each odd cycle, the animation plays in reverse (100% to 0%). On each even cycle, the animation plays forward (0% or 100%).

### animation-fill-mode

It specifies if the animation styles are visible before or after the animation plays. 

* `normal` - Default. The animation does not apply any styles to the element, before or after the animation.

* `forwards` - After the animation is finished, the styles defined in the final keyframe (100%) are retained by the element.

* `backwards` - Before the animation (during the animation delay), the styles of the initial keyframe (0%) are applied to the element.

* `both` - `forwards` with `backwards`.

### animation-play-state

Two values: `running` and `paused`.

It specifies whether the animation is `playing` or `paused`. **Resuming a paused animation starts the animation where it was left off. But if pause an animation, the element style will return back to its origin.**

Example:

{% highlight css %}
div:hover {
  animation-play-state: paused;
}
{% endhighlight %}

## Multiple Animations

Add multiple animations to a selector with comma:

{% highlight css %}
div {
  animation: animationA 2s, animationB 2s;
}
{% endhighlight %}

## Refs

* [Imooc 十天精通CSS3](http://www.imooc.com/learn/33)
* [CSS Animation for Beginners](https://robots.thoughtbot.com/css-animation-for-beginners#animation-iteration-count)
* [CSS3 animation-timing-function Property](http://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp)
