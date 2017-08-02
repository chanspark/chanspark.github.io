---
layout: post
title:  "XMLHttpRequest, Node"
description: "기본 지식 쌓기"
author: chanspark
image: " "
date:   2017-07-04 20:30:00 +0900
tags: [wilt, ajax, node]
comments: true
---

WILT(What I Learned Today)의 생존일기? 입니다. 작업하며 겪었던 에러 등을 해결하기 위한 고민의 흔적들을 저장하는 지극히 개인적인 포스트 입니다. 

## XMLHttpRequest(), AJAX
서버와 정보를 주고 받기 위해 사용되는 기본적인 javascript 객체입니다. ajax와 동일한 기능을 한다고 볼 수 있습니다. 마이크로소프트에서 만든 만든 객체이며 현재는 웹에서 비동기적으로 데이터를 주고 받게 해주는 매우 중요한 역할을 하고 있습니다. 실제로 흔히 사용되는 ajax는 Asynchronous JavaScript and XML의 약자 입니다. 여기서 AJAX는 기본적으로 XML객체를 이용하는 통신이라는 것을 알 수 있습니다. 물론 XML만 사용하는게 아니라 JSON도 사용할 수 있다는데, 이에 대해서는 더 자세하게 알아보도록 하겠습니다. 오늘은 여기까지... ㅇㅅㅇ

참고: [MDN - XMLHttpRequest](https://developer.mozilla.org/ko/docs/XMLHttpRequest), [생활코딩 - AJAX](https://opentutorials.org/course/1375/6843)

## Node.js

### NPM
Node.js 의 앱스토어라고 생각하면 된다. 그만큼 node 관련 모듈이 많이 저장되어 있고, 설치도 `npm install module-name` 으로 매우 쉽게 할 수 있습니다.

### package.json
node 프로젝트에서 npmd 통해 설치한 모듈의 버전정보가 저장 되는 곳입니다. 회사에서는 하나의 프로젝트 파일을 팀원들과 공유해야하는데, npm 모듈이 수십, 수백가지 일경우 git 에 커밋/업로드 하는거 자체가 엄청난 시간을 소요하며, 다른 팀원이 clone 하는 일도 너무 번거로울 수밖에 없습니다. 그래서 git ignore 파일에서 노드 모듈은 모두 무시하고, 이 package.json 에 들어있는 호환되는 모듈 버전들의 리스트를 사용해서 모듈을 설치합니다. node 프로젝트는 대부분 clone 후 npm install 을 하면 로컬에서 테스트 하는데 문제가 없습니다(경험입니다. 별도의 세팅을 해줘야하는 경우도 있습니다.'php laravel등등..')

### devdependencies and dependencies 차이점
npm 모듈을 설치해보면 `npm install module-name` 을 입력해보셨을 겁니다. 그런데 어떤 모듈은 뒤에 `--save` 또는 `--save -dev` 를 붙이라고 설명해줍니다. 별 생각 없이 설치를 하다가 문득 이걸 알아봐야겠다 싶어서 검색을 해봤습니다. 

1. `install`은 모듈을 설치하고 종료되는 커맨드입니다. 
2. `--save`는 package.json 파일에 모듈의 버전 dependency(호환성)을 저장합니다. dependencies 오브젝트에 저장하게 됩니다.
3. `--save -dev`는 `--save`와 동일하지만 devDependencies 오브젝트에 저장합니다.

[블로그 참고](http://ohyecloudy.com/ddiary/2016/09/04/til-npm-install-save-or-save-dev/)

## Underscore JS
[Underscore JS](http://underscorejs.org)란  

## 오늘의 사이트
[면접 문제 은행](https://github.com/h5bp/Front-end-Developer-Interview-Questions/tree/master/Translations/Korean)

