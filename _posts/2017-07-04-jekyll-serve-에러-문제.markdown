---
layout: post
title:  "jekyll serve 에러 문제"
description: "jekyll에서 문제가 발생했다"
author: chans
image: "default.jpg"
date:   2017-07-04 20:30:00 +0900
tags: [jekyll]
---

## 로컬에서 jekyll serve 에러가 뜨다
퇴근하고 블로그 테마작업을 하려고했는데 이상하게 `jekyll-serve`가 안되네요 ㅠㅠㅠㅠ 마지막 작어 후 했던 건 맥북 OS 업데이트밖에 없는데... 아래는 관련 에러입니다.

```
/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/rubygems/dependency.rb:296:in `to_specs': Could not find 'jekyll' (>= 0) among 19 total gem(s) (Gem::LoadError)
```

찬찬히 뜯어보면 jekyll을 못찾고 있고 19가지 gem 도 못찾는다고 뜨는것 같네요. 이게 무슨일인지 싶어서 `ruby -version` 을 쳐서 확인해보니 기존에 rbenv 로 작업해놓았던 2.2 버전대가 아니라 2.3 버전대로 업그레이드가 되어져 있었습니다. 단순히 OS 업데이트로 인한 에러인지, 삽질하면서 2.3버전을 설치했는데 reboot 하지 않아서 업그레이드가 안되어 있던 에러인지... 감을 잡을 수가 없네요. 어쨌든 jekyll이가 없다니 또 설치를 해줬습니다. `gem install jekyll` 후 `gem install bundler`

```
jekyll serve
.....gems/ruby-2.3.4/gems/bundler-1.15.1/lib/bundler/spec_set.rb:87:in `block in materialize': Could not find rb-fsevent-0.9.8 in any of the sources (Bundler::GemNotFound)
```

이건 또 무슨 에러인지... 하... rb-fsevent라는건 Ruby 에서 사용하는 API 라고 합니다. 맥 OS 에서 파일 시스템 크롤링? 을 좀 더 쉽게 하기 위해서 사용되는 API지만 대부분의 gem 들이 이 API를 필수적으로 사용하지는 않지만, 있으면 사용한다고 합니다. 그런데 이게 왜 말썽일까요? 재밌는거는 `jekyll -version` 이라고 하면 위의 에러가 뜨고 `bundler -version` 이라고 하면 제대로된 값을 출력해 줍니다. 지킬을 아예 삭제했다가 다시 설치해볼까... `gem uninstall jekyll`, `sudo gem uninstall jekyll` bundler 도 함께 삭제해 줍니다. 일단 위에 저 에러가 왜 뜨는지 모르니 아예 새로 설치를 해보죠!! `gem install jekyll` 
......
흨 또 같은 에러가 뜹니다. 다시 찬찬히 구글링을 해본 결과 jekyll 을 첫 설치 하고 구동할때 `bundle exec jekyll serve` 명령어로 jekyll 파일에 포함되어있는 gemfile 을 실행시켜야 한다고 나와 있네요! 역시나 위의 명령어를 입력하니 `bundle install` 을 먼저 실행하라고 합니다. 
![alt text](../blogs/assets/20170704/1.png "아싸리")
뚜둔!!
뭔가 행복한 초록색 라인들이 가득하네요! 당장 코드를 실행합니다. `bundle exec jekyll serve --baseurl '' --watch`
여전히 문제가 있기는 합니다. `bundle exec`을 붙이지 않고 `jekyll serve` 를 하면 위의 rb-fsevent 호환성 문제가 자꾸 나타나네요. 제 맥에서만 일어나는 문제일 수도 있습니다. ㅠㅠㅠㅠ 일단 에러코드에서도 'bundle exec 을 에러난 커맨드 앞에 붙이면 문제가 해결될 수 있습니다.' 라고 뜨는 걸 보니 너무 큰 문제는 아닌가 봅니다?? 끗!