---
layout: post
title:  "ExpressJS, EJS 에서 SEO 적용하기"
description: "JS 초짜가 살아남는법"
author: chans
image: "20170630-1-main.jpg"
date:   2017-06-30 11:30:00 +0900
tags: [jekyll, express, ajax]
comments: true
---


## 생각
회사 사이트에 마케팅을 위한 블로그 형식에 페이지가 있습니다. 마케팅을 위해서라면 SEO가 무엇보다 중요하기 때문에 블로그 페이지에서만이라도 각종 `meta` 태그를 적용시켜보기로 했습니다.
우선 사이트가 express js 와 ejs 를 기반이기 때문에 템플릿 엔진으로 DOM을 구현하면 될것 같습니다.

express js를 통해서 생성된 라우트 파일을 열어보면 블로그 관련 소스가 있습니다.
```javascript
router.get('/blogs/:slug', function(req, res, next) { // 'blogs/한글-URL-입니다' 로 접속할 경우 라우팅 함수에 들어옵니다.
    var slug = req.params.slug; // slug 변수에 URL의 slug 파라미터를 할당합니다.
    var _title = slug.replace(/-/g, " "); // title 태그에는 slug의 하이픈(-)을 제거해주고 변수로 할당합니다.
    res.render('./sub/blogs-show', {  // blog-show.ejs  파일을 렌더링합니다.
        // ejs 에서 사용하게 될 변수들
        'slug': slug,
        title : _title,
        url : webUrl + "blogs/" + slug,
        description : "description",
    });
}
```

이렇게 전달받은 변수들을 토대로 마크업에 원하는 위치에 뿌려주면 됩니다.
```html
?
```



### SLUG?
제 영역이 아닌지라 `slug`에 대해서도 알아봤습니다.



