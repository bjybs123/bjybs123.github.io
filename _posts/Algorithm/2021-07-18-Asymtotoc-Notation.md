---
title:  "Asymptotic Notation(점근 표기법)"
excerpt: "Big - O Notation(빅 - 오 표기법)"

categories:
  - Algorithm
tags:
  - algorithm
  - time complexity
last_modified_at: 2021-07-18
---

<script type="text/x-mathjax-config">MathJax.Hub.Config({ tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]} });</script><script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>

**Asymptotic Notation**(점금 표기법)이란 알고리즘의 시간적, 공간적 성능과 효율을 측정하기 위함에 있다.

대표적으로 **Big- Θ, Big - Ω, Big - O**표기법이 있다. 여기서 자세히 살펴볼 표기법은  **Big -O**이다. 왜냐하면 Big - O표기법을 가장 많이 사용하기 때문이다.    
<br/>
<br/>
**Big - O Notation**

빅-오 표기법은 **asymptotic upper bound**(점근적 상한선)을 의미한다. 쉽게 말하면 알고리즘의 속도 혹은 공간 복잡도가 나빠도 해당 지표와 같거나 더 좋다는 뜻이다.

빅-오 표기법을 주로 사용하는 이유는 알고리즘의 시간 복잡도를 얘기할때 주로 최악의 경우를 얘기 하기 때문에 즉, 알고리즘이 최악의 경우의 얼마나 느린가를 고려해서 어떤 알고리즘을 이용해야 최선인지를 얘기 하기 위함이다. 

빅-오 표기법의 수학적인 정의와 그래프를 통해 이해하면 더 직관적이다. 

빅-오 표기법의 수학적 정의는 아래와 같다. 

$O(g(n))$ = { $f(n)$: there exist positive constants $c$ and $n0$ such that $0$ $<=$ $f(n)$ $<=$ $cg(n)$ for all $n$ $>= $ $n0$} 

$n0$보다 큰 $n$에 대해서 $0 <= f(n) <= cg(n)$을 만족시키는 상수 $c$가 존재한다.
<p align="center">
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F3CP0T%2Fbtq9Nue0zt7%2FKfNDN1PF3dpMAhzr0CvI71%2Fimg.png">
</p>
해당 그래프에서 y축을 실행 횟수라고 생각하면 어떤 알고리즘의 시간 혹은 공간 복잡도는 $f(n)$이다. 그의 상한선인 $cg(n)$을 은 해당 알고리즘에서 최악의 경우 이다. 그래프를 보면 $cg(n)$이 y축 기준으로 위에 있기때문에 최악의 경우인것을 확인할 수 있다.

<br/>
**Asymptotic Complexity**
<p align="center">
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcg3sZT%2Fbtq9Kvx8dQN%2FMycKQ2eisIHlVNuY8xKbhK%2Fimg.jpg">
</p>

알고리즘의 시간 혹은 공간복잡도를 얘기할때 가장 많이 사용되는 표기법은 사진과같다. 해당 그래프들은 고교 수학시간에 배운 함수 그래프를 생각하면 쉽다.

<br/>
Ref.

asymptotic complexity, [https://www.tutorialspoint.com/asymptotic-complexity](https://www.tutorialspoint.com/asymptotic-complexity)  

Charles E. Leiserson. Ronald L. Rivest. Clifford Stein 『Introduction to Algorithms. Third Edition.』 The MIT Press

Big-O Notation(빅 오 표기법) 대표적인 점근 표기법, [https://joycestudios.tistory.com/63](https://joycestudios.tistory.com/63)