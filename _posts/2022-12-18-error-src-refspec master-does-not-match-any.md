---
title: 깃 에러 src refspec master does not match any
categories: [Git]
tags: [Git, GitHub, Git Error]
---

## 발단

Github에 올리기 위해 `git push origin master` 를 했는데 error: src refspec master does not match any 가 발생했다. 위 에러 해결법 뿐만 아니라 꼬리물기식으로 여러가지 찾아봤다.

## 전개

위 에러가 나오는 이유는 많지만 나의 경우는 branch 이름이 main인데 git push origin master 즉, master라는 이름의 branch로 push 해서 발생했다. 아무래도 main branch를 master로 사용하는 게 습관이 돼서 당연히 master라고 생각했다. 원래는 master가 default branch였지만 지금은 main이 default branch로 바뀌었다. Black Lives Matter 운동으로 master/slave 등의 IT에서 사용되는 용어에도 정화가 필요하다는 의식이 생기고 있을 때 [Github](https://github.com/github/renaming)에서 2020년에 리포지토리의 기본 브랜치명을 master에서 main으로 변경했다.

**Black Lives Matter**

> [Black Lives Matter](https://ko.wikipedia.org/wiki/Black_Lives_Matter) 운동이란 아프리카계 미국인에 대한 경찰의 잔인함에 따른 사고에 대항하는 비폭력 시민불복종을 옹호하는 조직화된 움직임을 말한다.

그래서 이제 `git init` 을 하면 main이 default branch이다.

**origin? master?**

> 브랜치 이름으로 많이 사용하는 “master” 라는 이름이 괜히 특별한 의미를 가지는 게 아닌 것처럼 “origin” 도 특별한 의미가 있는 것은 아니다. `git init` 명령이 자동으로 만들기 때문에 사용하는 이름인 “master” 와 마찬가지로 “origin” 도 `git clone` 명령이 자동으로 만들어주는 리모트 이름이다. `git clone -o booyah` 라고 옵션을 주고 명령을 실행하면 `booyah/master` 라고 사용자가 정한 대로 리모트 이름을 생성해준다.

## 결말

해결법은 간단하다. 일단 `git branch` 로 branch 확인 후,
현재 branch가 main이라면 `git branch -m master` 로
main branch 를 master branch로 이름을 바꾼다.

현재 branch가 main이 아닌 다른 branch라면 `git branch 현재브랜치명 master` 로 바꿀 수 있다. 이름을 바꿨을 경우 저장소에도 알려줘야하기 때문에 `git push origin :main` 을 해줘야 한다. :로 이름이 바꼈다고 알려주는 것이다.

또 다른 방법으로는 `git checkout -b master` 로 main에서 master로 새로운 branch를 만드는 것이다.

## 정리

- default branch name은 main이다.
- main branch에서 master branch로 이름을 바꿔준다.
- main에서 master branch를 새로 만들어준다.

**참고자료**

> [Git 공식 참고자료](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EB%B8%8C%EB%9E%9C%EC%B9%98)  
> [Dillion Megida 포스팅](https://www.freecodecamp.org/news/error-src-refspec-master-does-not-match-any-how-to-fix-in-git/)
