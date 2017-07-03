---
layout: post
title:  "ExpressJS, AJAX 사용기"
description: "JS 초짜가 살아남는법"
author: chanspark
image: "20170630-1-main.jpg"
date:   2017-06-30 11:30:00 +0900
categories: 포스트
---

# ExpressJS 에서 AJAX호출을 통한 EJS 템플릿 작성
ejs 로 구축되어있는 회사 웹 서비스의 블로그에 SEO를 적용하려고 수많은 뻘짓을 하게 되었습니다. 그냥 '이렇게 할 수 있을텐데'라는 생각 하나만 가지고 구글링을 해나가며 포스트를 작성하는 것이니 글이 복잡하더라도 이해해주세요....

## 생각(이렇게 할 수 있지 않을까?!)
하하하하
```javascript
// membership type
/*
* length
*/
var chans = 1;
var value = $(input).val();
    console.log(value);
    var valueTrim = value.trim();
if (regPhoneNum.test(valueTrim) === true) {
        // 휴대폰 번호만 입력시 테스트
        if (length == 11 || length == 10) {
            validateSuccess($(input));
            registerType = "phone";
        } else {
            validateError($(input));
            registerType = "null";

        }
```
