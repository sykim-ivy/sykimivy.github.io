---
layout: post
title: Java 'String' isn't type, is Class
category: Java
tags: [Java]
---

## String 클래스
 - java.lang 패키지에 속한 클래스
 - 문자열 인스턴스 (문자배열, 문자 수, 필드, 메서드 등을 가진 클래스)에 대한 <strong>참조</strong>
 - String은 문자배열(private final char[]), 문자 수(private final int)을 final값으로 가지고 있어<br/>
   <strong>값을 변경시 다른 문자 배열을 참조하게 됨</strong>
 
