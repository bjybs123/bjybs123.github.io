---
title:  "Namespace (네임스페이스)"
excerpt: "Namespace란 무엇일까?"
categories:
  - Computer Science
tags:
  - computer science
  - namespace
last_modified_at: 2021-09-11
---

우리는 Computer Science 혹은 Coding을 할 때 **Namespace**라는 Term을 많이 볼 수 있다. 특히 C++를 처음 배울 때 "Hello World!"를 출력하기 위해서도 std라는 namespace 안에 있는 cout 함수를 이용하여 출력을 한다.  

C++를 예로 들면 변수와 함수등을 구분하기 위해서 우리는 **식별자 (identifier)**라는 것을 사용하게 된다. 프로그램이 커짐에 따라서 많은 Header를 include 시키고 라이브러리를 사용하게 되면 간혹 식별자가 겹쳐 프로그램이 충돌하는 일이 발생할 수 있다.  

이를 방지하기 위해서 Header 안에 Namespace를 만들어 해당 Namespace 안에 있는 변수 혹은 함수들을 Namespace를 통해서 접근을 하게 하여 문제 해결이 가능하다.  

쉽게 말하면 Header 안에 Namespace라는 Scope가 있고 그 안에 있는 변수 혹은 함수들은 다른 Namespace의 변수 혹은 합수와 식별자 즉, 이름이 겹칠 수 있기 때문에 Namespace라는 것을 통해서 접근이 가능하게 하는것이다.  


<br/>
# Namespace를 정의 하는 방법

C++ 프로젝트에 foo.h Header가 있다고 가정하자.  
```
#pragma once

namespace cat
{
	int age;
	int hospitality;
}

namespace dog
{
	int age;
	int hospitality;
}
```

<br/>
# Namespace 접급 방법

C++ 프로젝트에 foo.h를 include 시켜 cpp파일에서 접근해보자.  

namespace를 접근 하기 위해선 범위 지정 연산자 (Scope resolution operator) **::** 를 사용하면 된다.  
```
#include "foo.h"

int main()
{
	cat::age;
	cat::hospitality;
	dog::age;
	dog::hospitality;
}

```