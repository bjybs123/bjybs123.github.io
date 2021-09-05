---
title:  "Selection Sort (선택 정렬)"

categories:
  - Algorithm
tags:
  - algorithm
  - sort
  - selection sort
last_modified_at: 2021-07-22
---

<script type="text/x-mathjax-config">MathJax.Hub.Config({ tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]} });</script><script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>


선택정렬은 사람이 정렬하는 방법과 가장 유사한 정렬 알고리즘이다. 

0번째 원소부터 N - 1번째 뭔소 기준으로 우측 원소들의 가장 작은값과 대소비교를 하여 교환을 해주는 방식이다. 

선택정렬은 모든 경우에서 $O(n^2)$이라는 느릭 속도를 자랑하지만 선택 정렬 또한 특정 경우에 뛰어난 퍼포먼스를 보여주는 경우가 존재한다.

일단 첫번째로는 사람의 정렬 방법과 유사하다는 점에서 **단순하다**는 점이 장점이다. 또, 가용한 메모리가 한정적인 경우에서 **in-place 알고리즘**이기 때문에 효과적이다. (in-place 알고리즘에 대해서 나중에 자세하게 다뤄본다). **descending -order (내림차순)으로 정렬된 데이터**에 대해서 **Ascending - order(오름차순)으로 정렬**할 경우 최적의 효율을 낸다.

물론 선택정렬은 느린 정렬에 속한다. (자주 사용되는 정렬을 모두 정리한 다음에 특정 케이스에 대해서 적합한 정렬에 대해서 포스팅할 예정이다)

<p align="center">
<img src="https://en.wikipedia.org/wiki/File:Selection-Sort-Animation.gif">
</p>

**선택 정렬의 동작 순서**
-   0번째 원소부터 N - 1번째 원소를 기준으로 우측 원소들에서 가장 작은 원소를 integer형 변수 min\_vol에 저장한다.
-   기준이 되는 원소와 min\_vol의 대수비교를 통해 기준 원소가 min\_vol보다 크다면 두 원소를 SWAP함수를 통해 교환한다. 

**선택 정렬의 시간, 공간 복잡도**

**시간 복잡도** | | | **공간 복잡도**
편균 (Average) |최선 (Best) | 최악 (Worst) |
$O(n^2)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$

**Selection Sort (선택 정렬) C++ 코드**

```
#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;

void SWAP(int* a, int* b)
{
	int temp;
	temp = *a;
	*a = *b;
	*b = temp;
}

void SelectionSort(int* arr, int max_vol)
{
	int min;
	int i, j;
	for (i = 0; i < max_vol - 1; ++i)
	{
		min = i  + 1;
		for (j = i + 1; j < max_vol; ++j)
		{
			if (arr[min] > arr[j])
				min = j;
		}
		if (arr[i] > arr[min])
			SWAP(&arr[i], &arr[min]);
	}
}

int main()
{
	
	srand(unsigned int(time(NULL)));

	int arr[10] = { 0, };

	int i;
	for (i = 0; i < sizeof(arr) / sizeof(int); ++i)
		arr[i] = rand() % 100;

	cout << "before sort\n";
	for (i = 0; i < sizeof(arr) / sizeof(int); ++i)
		cout << arr[i] << "	";
	cout << '\n';

	SelectionSort(arr, sizeof(arr) / sizeof(int));
	cout << "after sort\n";
	for (i = 0; i < sizeof(arr) / sizeof(int); ++i)
		cout << arr[i] << "	";
	cout << '\n';
}
```

**고찰**

각 정렬의 장단점에 대해서 공부를 하고있지만 막상 코딩을 할 때 어떤 상황에서 어떤 정렬 알고리즘을 사용해야 하는지 판단이 안 설 것 같다. 시간, 공간복잡도에 대해서도 이해도가 깊지 않을 것 같아서 따로 시간을 들여서 공부가 필요할 것 같다.

<br/>
Ref.

Selection Sort / [https://en.wikipedia.org/wiki/Selection\_sort](https://en.wikipedia.org/wiki/Selection_sort)