---
layout: post
title: "Create calendar with Moment.js"
description: ""
author: chanspark
image: ""
date: 2017-09-27 20:30:00 +0900
tags: [study, wilt]
comments: true
published: false
---

## 달력을 만들자
날짜 계산은 어렵다. JS Date 객체를 활용하기에도 머리아프다. 그냥 Moment.js를 활용해보자.  
Moment.js를 활용해서 날짜, 시간 관련 에러는 따로 생각하자. 달력만드는데만 집중하자.  

### 생각
1. `this week`을 구함. `moment().isoWeek()`.
2. `this week`에 6주를 더함. `for`문으로 6번 돌아서 각각 객체안 배열로 넣음. `this week`에서 `weeks` 배열로 만듦. isoWeek값이 속하는 `month`와 `year`값도 저장함.  
       
    ```
    weeks = [
	    {
	    	week: 0, 
	    	month: 0,
	    	year: 0
		}, 
		{
			week: 0, 
	    	month: 0,
	    	year: 0
    	}
    	... 
	]
    ``` 
3. `today`값을 구함. 이를 `calendar`객체에 추가해줌. `weeks`배열도 추가해줌.

	```
	calendar = {
		weeks : [...],
		today : 0,
		day : today.isoWeekday()
	}
	```
4. `events` 배열 생성, schedule api를 통해 불러온 데이터를 토대로 지정된 날짜마다 event를 추가.   
	
	```
	events = [
		date: 0,
		type: className
	]
	```
5. `calendar` 객체를 통해서 달력을 생성한다.  
	굉장히 애매하다. ejs를 사용해서 자동으로 템플릿을 생성하는 방법이 있고, pure JS를 사용해서 만들 수도 있다.  
6. isoDate값으로 받아온 week값을 이용해서 한주씩 마크업을 append해나가면 된다.
7. month값이 바뀔경우, month 마크업을 append 시킨다.
8. 












