---
title:  "Quick Sort (퀵 정렬) C++"

categories:
  - Algorithm
tags:
  - algorithm
  - sort
  - quick sort
last_modified_at: 2021-08-01
---

<script type="text/x-mathjax-config">MathJax.Hub.Config({ tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]} });</script><script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>

평균적으로 빠른 속도를 자랑하는 정렬 알고리즘이다. 

퀵 정렬은 Merge Sort (합병 정렬)과 같이 **divide and conquer (분할 정복) 알고리즘**이다. 

같은 분할 정복 알고리즘인 합병 정렬과는 다르게 **In-place 알고리즘**이다. 하지만 여전히 재귀 호출로 인한 스택 메모리 공간이 필요하기 때문에 **$O$($logn$)의 공간 복잡도**를 가진다. 

퀵 정렬은 합병 정렬과 다르게 추가적인 메모리 공간이 필요 없다. 또한 퀵 정렬은 **균등하게(반으로) 분할**하는 합병 정렬과 다르게 **비균등하게 분할**을 하게 된다.  

퀵 정렬을 정렬 알고리즘에서 빠른 속도를 내주는 알고리즘이다. 피벗(기준)을 어디로 잡느냐에 따라 달라지지만 평균적으로 **$O$($nlogn$)**의 시간 복잡도를 가진다. 

<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Sorting_quicksort_anim.gif/220px-Sorting_quicksort_anim.gif">
</p>

퀵 정렬은 pivot을 사용하게 된다. pivot은 분할을 할 때 기준이 되고 분할을 한 후 대소 비교의 기준이 된다. 쉽게 기준이라고 생각하면 쉽다. pivot을 어떻게 설정하냐에 따라 알고리즘의 속도가 달라질 수 있다. pivot설정에 대해서 아직도 연구 중이며 본 퀵 정렬의 pivot은 최좌단 원소로 한다. 

퀵 정렬 작동 방법

-   배열의 맨 왼쪽 원소를 pivot으로 설정하고 pivot기준 왼쪽엔 pivot 보다 작은 원소 오른쪽엔 pivot 보다 큰 원소로 위치한다. 
-   pivot기준 좌측과 우측을 동일한 방법으로 분할하여 정렬한다. 
-   위 과정을 분할하여 정렬하고자 하는 배열의 크기가 1보다 작거나 같은 경우전까지 반복한다. 

Quick Sort (퀵 정렬) C++ 코드

```
#include <iostream>

using namespace std;

void SWAP(int* a, int* b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}

int quick_sort(int* arr, int left, int right)
{
	int pivot;
	int low, high;
	pivot = arr[left];
	low = left + 1;
	high = right;
	while (low <= high)
	{
		while (arr[low] <= pivot && low <= right)
		{
			++low;
		}
		while (arr[high] => pivot && high >= left + 1)
		{
			--high;
		}

		if (low <= high)
		{
			SWAP(&arr[low], &arr[high]);
		}

	}
	SWAP(&arr[left], &arr[high]);


	return high;
}

void partition(int* arr, int left, int right)
{
	if (left < right)
	{
		int q = quick_sort(arr, left, right);

		partition(arr, left, q - 1);
		partition(arr, q + 1, right);
	}
}

int main()
{
	int arr[10] = { 3, -1, 2, 9, 13, 29, 94, 29 ,9, 11 };
	for (int i = 0; i < 10; ++i)
		cout << arr[i] << "	";
	partition(arr, 0, 9);
	cout << "\n";
	for (int i = 0; i < 10; ++i)
		cout << arr[i] << "	";
}
```

<br/>
Ref.

Quick Sort / [https://en.wikipedia.org/wiki/Quicksort](https://en.wikipedia.org/wiki/Quicksort)