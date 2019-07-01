---
layout: post
title: [Error][GitHubPages] Page build failed: Unknown tag error
category: GitHubPages
tags: [error][GitHubPages]
---

## Page build failed: Unknown tag error

{% highlight %}
Page build failed: Unknown tag error
If your GitHub Pages code contains an unrecognized Liquid tag, your GitHub Pages site will not build.

If your GitHub Pages site fails to build because of an unrecognized Liquid tag, you'll get an email that looks like this:

Subject: Page build failed

The page build failed with the following error:

The tag `fake_tag` in `index.html` is not a recognized Liquid tag.
{% endhighlight %}
<br/>
포스팅에 위와 같이 에러가 발생했다. [에러 상세 페이지](https://help.github.com/en/articles/page-build-failed-unknown-tag-error) <br/>
이럴 경우 포스팅이 올라가지 않는다. 'GitHub > Setting'로 가서 확인했다ㅜㅜ<br/>
<br/>
주로 포스팅에 태그 문법이 틀려서 발생하는 듯하다. <br/>
나의 경우 포스팅 내 소스 코드에 '{% endlight %}'로 써야하는데 마지막 '%'기호를 빼먹어 <br/>
'{% endlight }'로 닫아버려 발생한 문제였다. <br/>
<br/>
저처럼 글이 안 올라간다고 삽질하지 않기를 바랍니다...ㅠㅠ<br/>

## Refs
* [github io 마크다운 태그 삽질] (https://hotbloodturtle.github.io/git/2018/03/02/markdown-syntax/)







