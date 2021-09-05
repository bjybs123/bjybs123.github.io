---
title:  "Insertion Sort (삽입 정렬) C++

categories:
  - Algorithm
tags:
  - algorithm
  - sort
  - insertion sort
last_modified_at: 2021-07-18
---

<script type="text/x-mathjax-config">MathJax.Hub.Config({ tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]} });</script><script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>

필자가 항상 헷갈려 하는것이 정렬 알고리즘이다.

이제까지 속도를 고려하지 않고 Bubble Sort가 손에 익기 때문에 사용을 해왔다. 이제 제대로 공부할 시기가 왔기도 했고 백준 문제를 풀때 정렬 속도 때문에 틀리는 경우가 빈번해 졌기 때문에 이번 기회에 하나씩 구현해보면서 손에 익히는 과정을 가지도록한다.

삽입 정렬은 최선의 케이스에서 시간 복잡도가 $O$($n$)라는 빠른속도를 가지고 있지만 최악의 케이스에서는 $O$($n^2$)라는 느린 속도를 가진다.

삽입 정렬은 **이미 정렬된 데이터**를 정렬할때 **매우 유용하게 사용**된다.

<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/e/ea/Insertion_sort_001.PNG">
</p>


**삽입 정렬의 동작 순서**

-   integer형 배열의 1번째(2번째 원소)원소의 값을 integer형 변수 Key에 저장한다.
-   해당 원소기준 왼쪽부터 자신과 대소 비교를 하여 자신보다 작은 원소를 만날때 까지 원소를 오른쪽으로 이동시킨다.
-   해당 자리에 Key값을 저장시킨다.
-   다음 원소를 Key값에 새로 저장하고 마지막 원소까지 위 과정을 반복한다. Loop (1번째 원소 ~ 마지막 원소)

<br>
**삽입 정렬의 시간, 공간 복잡도**

**시간 복잡도** | | | **공간 복잡도**
편균 (Average) |최선 (Best) | 최악 (Worst) |
$O(n^2)$ | $O(n)$ | $O(n^2)$ | $O(1)$

<br/>
**Insertion Sort(삽입 정렬) C++ 코드**

```
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;


void InsertionSort(int* sort_arr, int index)
{
	int i, j;
	for (i = 1; i < 10; ++i)
	{
		int target = sort_arr[i];
		for (j = i - 1; j >= 0 && sort_arr[j] > target; --j)
		{
			sort_arr[j + 1] = sort_arr[j];				
		}
		sort_arr[j + 1] = target;
	}
}

int main()
{
	srand((unsigned int)time(NULL));
	int arr[10];
	int i;
	for (i = 0; i < 10; ++i)
		arr[i] = rand() % 100;			//0 ~ 99

	cout << "before sort\n";
	for (i = 0; i < 10; ++i)
		cout << arr[i] << '	';
	cout << '\n';
	
	cout << "after sort\n";
	InsertionSort(arr, 10);
	for (i = 0; i < 10; ++i)
		cout << arr[i] << '	';
	cout << '\n';

}
```

<br/>
**고찰**

정렬에 대해서 별로 크게 의미를 두지 않았다. 왜냐하면 문제가 주어지면 해당 문제를 푸는 과정에 있어서 정렬 알고리즘은 그냥 작은 일부분이라고 생각했고 "정렬만 되만 되지"라는 생각을 가지고 있었다. 거기에 정렬 마다 속도가 빠르고 느리다는 생각을 가지고 있었지만 삽입 정렬은 느린 정렬 퀵 정렬은 빠른 정렬이라고만 생각하고 있었는데 삽입 정렬이 가장 효율이 좋을때도 있다는 사실을 공부하고 살짝 충격을 먹었다. 각 정렬마다 장단점을 파악하고 어느 상황때 어느 정렬을 사용해야 가장 효율적인지를 파악하면 나중에 정렬 부분에서 훨씬 더 좋은 퍼포먼스를 보여줄 수 있을거라 기대를 하게 되었다.

<br/>
Ref.

삽입 정렬이란 /  [https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html)

삽입 정렬 / [https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85\_%EC%A0%95%EB%A0%AC](https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85_%EC%A0%95%EB%A0%AC)