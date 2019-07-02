---
layout: post
title: 자바 타입별 Default Value
category: Java
tags: [Java]
---

## 타입별 자바 초깃값(default value)
<br/>

|타입|Default value|
|:---|:---|
|char | \u0000 |
|참조형 | 공백 참조 또는 null|
|byte |(byte)0|
|short|(short)0|
|int | 0|
|long | 0L|
|float | 0.0f|
|double | 0.0d|
|boolean | false |

<br/><br/>
클래스 변수(=필드, 프로퍼티) 선언후 초기화하지 않았을 때나, 배열 생성시 각 요소에 넣어지는 default값<br/>
cf) 메서드 내부에 선언한 지역변수는 default값으로 초기화되지 않음<br/>
<br/>
