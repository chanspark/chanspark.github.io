---
layout: post
title: "[React]TodoMVC + redux"
description: ""
author: chans
image: ""
date: 2017-09-15 20:30:00 +0900
tags: [study, wilt]
comments: true
published: false
---

## redux로 변환
action -> container component -> main.js <- store[reducer]  
화살표는  import 되는 경로이다.  
결과적으로 store에서 action을 접근할 수 있다.

axios 는 비동기처리이므로 액션으로 감?  

action 에서 ajax처리를 다 함. 객체안에 액션을 dispatch 하는 동작이 들어감.
비동기라서 그런가...
객체가 아닌 비동기 처리일 경우 함수만 반환할 수 있음.

action은 어떤것도 임포트하지 않음. 즉 컨테이너의 값을 알 수 없음. 오로직 단방향!!!

redux thunk 덕분에 액션을 가져와서 함수를 사용하는게 가능함.

dispatch -> getState() 사용가능

액션 대문자/소문자 가려서 사용하는게 편함.  

리듀서에는 switch case를 통해서 type별로 다른 함수를 돌린다.  

reducer 에서는  store에서 제공하는 prevstate만 참고 가능하다.

에러가 있음::ㅜ reducer 에서 default prevState값을 무조건 지정해줘야한다.

## Immutability Helper
[참고](https://github.com/react-study/reactStudy/blob/master/06_TodoApp2/README.md) 
prevState.todos = newTodos
prevTodos.todos[0].isDone = false 이런 방식은 넘나 넘나 리소스가 많이 든다.

고무곰님의 todoReducer에서 작성한 방법에 따른면, 

```
const initialState = {key, value; key, value .... }

const TodoReducer = (prevState = initialState, action) => {
case 'ABC':
	return Object.assign({}, prevState, {
		todos: action.todos
	});
	....
}
```

위 방법에서 prevState를 토대로 object.assign으로 새로운 객채를 만듦.  
prevState.todos. ... 하면서 찾아가는것보다 리소스가 훨씬 덜 드는 방법중 하나임.

기존 객체의 내용이 업데이트 될경우, 새로운 객채를 만들게 된다. 기존의 객체는 사라진다! (garbage collector). Immutable, 불변객체는 내가 한번 생성한 객체를 다시 수정할 일이 없기때문에 이렇게 부른다.

[Immutability Helper](https://github.com/kolodny/immutability-helper)

```
// import update from 'react-addons-update';
import update from 'immutability-helper';

const state1 = ['x'];
const state2 = update(state1, {$push: ['y']}); // ['x', 'y']

// 물론 배열일경우 더 쉽다.
// 객체에 사용할 경우 매우 좋음!
```

Object.assign 방법의 문제는 얕은 복사만 가능하다는 것이다. (초반에 배운것 중 하나)  
depth가 많아질 수록 recursive하게 참조, 참조, 참조를 계속 해야하는 문제가 있는데 이를 해결해 주는게 immutability helper.

```
import update from 'immutability-helper';

const newData = update(myData, {
  x: {y: {z: {$set: 7}}},
  a: {b: {$push: [9]}}
});

// x.y.z = 7
// a.b = [... 9]
```
우왕 짱싄긔 개 편하다!!

요 기능은 보통 리듀서에서 많이 사용된다 ㅇㅅㅇ


## 낙관적 업데이트
정상적으로 서버와 송수신이 이러지 것이라 믿고 일단 업데ㅣ티터 

서버에 요청을하고 응답이 돌아오면 반영을 함. 하지만 인터넷이 느릴경우? 서버에 데이터는 쌓이지만, 사용자는 모름. 응답이 없으니 계쏙 업데이트를 요청++++ 

따라서, 일단 화면에 가기 전에 사용자의 요청을 처리해줌 (카톡 전송, 댓글 등등..)  
예로 
그리고 서버에서 완료 confirm이 오면, 그때 실제 업데이트 

리덕스 + 낙관적 업데이트 굳 

리덕스일경우 action -> dispatch -> type: TEMPORAL로 해서 새로운 데이터를 그린다.
그다음 axios를 통해서 dispatch롤 보낸다



















