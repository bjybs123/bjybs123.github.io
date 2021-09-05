---
title:  "Bubble Sort (버블 정렬) C++"

categories:
  - Algorithm
tags:
  - algorithm
  - sort
  - bubble sort
last_modified_at: 2021-07-23
---

<script type="text/x-mathjax-config">MathJax.Hub.Config({ tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]} });</script><script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>

거품 정렬 혹은 버블 소트라고 불리는 Bubble Sort는 개인적으로 구현하기 가장 쉬운 알고리즘이다. 그렇기 때문에 현재 필자가 가장 많이 사용하는 정렬 알고리즘이다.

버블 소트는 왼쪽부터 작은 원소를 하나씩 정렬시키는 정렬이다. 그렇게 하기 위해서 반대쪽 원소부터 왼쪽까지 인접한 원소끼리 대소 비교 및 교환한다.

버블 소트는 **구현하기 쉬운 장점**이 있지만 **불필요한 교환**이 이루어진다는 점이 단점이다. 

**버블 소트의 동작 순서**

-   0번째 원소부터 N - 1번째 원소를 기준으로 잡는다.
-   최우단에서부터 인접한 원소들의 대소 비교를 통하여 작은 원소를 기준이 되는 위치에 정렬한다

**버블 소트의 시간, 공간 복잡도**

**시간 복잡도** | | | **공간 복잡도**
편균 (Average) |최선 (Best) | 최악 (Worst) |
$O(n^2)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$

**Bubble Sort (버블 소트) C++ 코드**

```
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

void SWAP(int* a, int* b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}

void BubbleSort(int* arr, int max_vol)
{
	int i, j;

	for (i = 0; i < max_vol; ++i)
	{
		for (j = max_vol - 1; j > i; --j)
		{
			if (arr[j] < arr[j - 1])
			{
				SWAP(&arr[j], &arr[j - 1]);
			}
		}
	}
}

int main()
{
	srand(unsigned int(time(NULL)));
	int arr[10] = { 0, };
	int i = 0;

	for (i = 0; i < 10; ++i)
	{
		arr[i] = rand() % 100;
	}

	for (i = 0; i < 10; ++i)
		cout << arr[i] << "	";
	cout << '\n';

	BubbleSort(arr, 10);
	for (i = 0; i < 10; ++i)
		cout << arr[i] << "	";
	cout << '\n';

}
```

<br/>
Ref.

Bubble sort / [https://en.wikipedia.org/wiki/Bubble\_sort](https://en.wikipedia.org/wiki/Bubble_sort)