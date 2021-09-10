---
title:  "String Class : 기본과 메소드"
excerpt: "String Class의 기본과 주요 메소드에 대해서 알아보자."
categories:
  - C++
tags:
  - c++
  - string
  - methods
last_modified_at: 2021-08-11
---

C 스타일 문자열 (char\*, char \[\])에 익숙한 나로서 C++의 string 클래스보다 C 스타일 문자열이 아직까지 편하다.
개강도 다가오기 때문에 **string 클래스**에 대해서 정리를 해보자.

먼저, **C 스타일 문자열의 단점**에 대해서 얘기해보자. 

C 스타일 문자열은 내가 저장하고자 하는 **문자열의 길이보다 1 크기의 길이가 더 필요하다**.
왜냐면 C 스타일 문자열에서 문자열의 끝을 나타내 주는 **NULL Character ('\\0')가 필요**하기 때문이다. 
이러한 특성 때문에 **문자열의 크기에 대해서 신경**을 써줘야 된다.
또한 동적으로 메모리를 할당했을 경우 할당 해제를 해주지 않으면 **Memory Leak이 발생하기 쉽다**. 

String 클래스는 말 그대로 클래스이다. String 클래스의 객체가 우리가 통상적으로 다루게 되는 "문자열"이다.
String 클래스를 사용하기 위해선 string헤더를 include 해줘야 한다. 하지만 string 헤더는 iostream 헤더에 포함되어 있기 때문에 iostream 헤더를 include 할 경우는 추가적으로 include 할 필요는 없다. 

String 클래스는 기존 C 스타일 문자열에서 느낀 불편을 다소 해결해준다. NULL Character를 삽입할 필요도 없고 다양한 메서드들이 존재하고 메모리에 관해서 신경 쓸 일도 많이 줄어들었다.
하지만 C 스타일 문자열이 속도가 더 빠르다는 장점이 있다. 

<br/>
**String 객체 생성**

```
string str;
string str1("문자열");
string str2 = "문자열";
```

위와 같이 **초기화 없이 str객체를 생성할 수 있다**.
클래스를 공부했다면 **선언과 동시에 Constructer (생성자)를 이용해 초기화하는** 방법과 **대입을 이용해 초기화하는** 방법이 있다. 

**String 입력**

```
string str;
cin >> str;     //white character전까지 입력
getline(cin, str);     //한 줄 통째로 입력
getline(cin, str, '문자');	//문자전까지 입력
```

String 객체를 입력받을 때 가장 많이 이용되는 두 방법이다. 먼저 cin객체를 이용해서 입력받는 방법은 White Character (' ', '\\t', '\\n') 전까지 입력을 받는다는 사실을 잊지 말자. 반면에 getline함수를 이용할 경우 '\\n'문자 전 즉, 한 줄을 통째로 입력을 받는다. 

**String 출력**

```
String str("I love jiyong");
cout << str;     //I love jiyong
```

string 객체의 출력은 cout 객체를 이용해 출력이 가능하다.

**String의 주요 메소드**

```
string str("Conquer");
```

객체 str을 생성자를 이용하여 "Conquer"로 초기화.

```
//String 객체 인덱싱 및 특정 문자 반환
cout << str.at(5) << '\n';	//e
cout << str[5] << '\n';	//e
cout << str.front() << '\n'; //C
cout << str.back() << '\n'; //r
```

str객체를 at메서드를 이용하여 인덱싱 하는 방법과 배열적 용법( \[\] )으로 인덱싱 하는 방법이 있다.
front와 back을 각각 제일 앞에 잇는 문자와 마지막 문자를 반환한다. 

```
//String 객체 문자열 조작 메소드
str.append("문자열");	//str 뒤에 "문자열" 삽입(연결)
str.append("문자열", n, m);	//"문자열"의 index : n 문자부터 m개의 문자열을 str 끝에 삽입(연결)
str.append(n, '문자');	//str 끝에 n개의 '문자' 삽입(연결)
str.insert(n, "문자열");	//index : n 문자 뒤에 "문자열" 삽입
str.replace(n, m, "문자열");	//index : n 문자부터 m개의 문자를 "문자열"로 대체
str.clear();	//문자열 모주 지움
str.erase();	//clear()과 동일
str.push_back('문자');	//문자열 맨 뒤에 '문자'삽입
str.pop_back();		//문자열 맨 뒤 문자 제거
```

문자열을 조작하는 메소드이다. C 스타일 문자열에서 대부분 직접 구현해야 하는 기능들인데 메소드를 이용하면 편리하게 원하는 기능을 사용할 수 있다. 

**이외의 더 많은 메소드들이 존재한다.**

본 포스트에서 다 다루지 못하고 위에 다룬 내용들도 함수의 원형 또한 모르니 **레퍼런스를 꼭 참고하기 바란다. **

ref.

string - C++ Reference / www.cplusplus.com


