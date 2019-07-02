---
layout: post
title: 자바 타입별 Default Value
category: Java
tags: [Java]
---

## 타입별 자바 초깃값(default value)
<br/>
<table>
<thead>
<tr>
<th align="left">타입</th>
<th align="left">Default value</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">char</td>
<td align="left">\u0000</td>
</tr>
<tr>
<td align="left">참조형</td>
<td align="left">공백 참조 또는 null</td>
</tr>
<tr>
<td align="left">byte</td>
<td align="left">(byte)0</td>
</tr>
<tr>
<td align="left">short</td>
<td align="left">(short)0</td>
</tr>
<tr>
<td align="left">int</td>
<td align="left">0</td>
</tr>
<tr>
<td align="left">long</td>
<td align="left">0L</td>
</tr>
<tr>
<td align="left">float</td>
<td align="left">0.0f</td>
</tr>
<tr>
<td align="left">double</td>
<td align="left">0.0d</td>
</tr>
<tr>
<td align="left">boolean</td>
<td align="left">false</td>
</tr>
</tbody>
</table>

<br/><br/>
클래스 변수(=필드, 프로퍼티) 선언후 초기화하지 않았을 때나, 배열 생성시 각 요소에 넣어지는 default값<br/>
cf) 메서드 내부에 선언한 지역변수는 default값으로 초기화되지 않음<br/>
<br/>
