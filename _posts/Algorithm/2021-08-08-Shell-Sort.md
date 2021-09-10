---
title:  "Shell Sort (쉘 정렬) C++"
excerpt: "화석 Shell Sort에 대해서 알아보자"
categories:
  - Algorithm
tags:
  - algorithm
  - sort
  - shell sort
last_modified_at: 2021-08-08
---


Shell Sort (쉘 정렬)은 Insertion Sort (삽입 정렬)을 **보완해서 나온 정렬 알고리즘**이다. 삽입 정렬은 데이터가 어느 정도 정렬된 상태에서 빠른 속도를 자랑한다.

삽입 정렬의 단점은 **데이터 삽입 과정에서 삽입할 위치가 멀리 있을 경우 데이터를 이동해야 하는 횟수가 늘어난다는 단점**이 있다. 이 단점을 보완하여 나온 정렬 알고리즘이 쉘 알고리즘이다. 

삽입 정렬은 배열의 1번째 원소부터 마지막 원소를 기준으로 잡고 좌측에 있는 원소를 하나하나 대소 비교를 통해 삽입할 위치를 찾는다. 쉘 정렬은 기준으로부터 좌측에 있는 원소와 대소 비교를 하되 **gap **즉, **일정한 간격을 두고 정렬**을 한다. gap을 두고 배열을 나누어 정렬한다고 생각하면 된다. 

<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/d/d8/Sorting_shellsort_anim.gif">
</p>

**Shell Sort (쉘 정렬) 작동 방법**

-   배열의 크기의 1/2를 첫 gap으로 한다.  **각 gap은 홀수여야 하므로 짝수 일 경우 1을 더해 홀수로 만들어준다. **
-   0번째부터 gap이전까지의 원소를 기준으로 gap만큼 떨어진 **연속적이지 않은 배열**로 나눈다.
-   각 연속적이지 않은 배열을 gap만큼 떨어진 원소들을 삽입 정렬로 정렬을 해준다. 
-   gap을 1/2배 해주어 위 과정을 gap이 0보다 클 때까지 반복한다. 

**Shell Sort (쉘 정렬) C++ code**

```
#include <iostream>

using namespace std;

void ShellSort(int* arr, int n)
{
	int gap, i, j, key;
	for (gap = n / 2; gap > 0; gap /= 2)
	{
		if (gap % 2 == 0)
			++gap;

		for (i = gap; i <= n; ++i)
		{
			key = arr[i];

			for (j = i; j >= gap && arr[j - gap] > key; j -= gap)
				arr[j] = arr[j - gap];

			arr[j] = key;
		}
	}
}
int main()
{
	int arr[15] = { 4, 8, 3, 6, 2, 1, 13, 15, 37, 56, 4, 2, 46, 24, 99};

	for (int i = 0; i < 15; ++i)
		cout << arr[i] << '	';

	ShellSort(arr, 14);

	cout << '\n';
	for (int i = 0; i < 15; ++i)
		cout << arr[i] << '	';

}
```

<br/>
Ref. 

쉘 정렬 / [https://gmlwjd9405.github.io/2018/05/08/algorithm-shell-sort.html](https://gmlwjd9405.github.io/2018/05/08/algorithm-shell-sort.html)

Shell Sort / [https://en.wikipedia.org/wiki/Shellsort](https://en.wikipedia.org/wiki/Shellsort)