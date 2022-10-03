> **`정렬되어 있는 리스트`**에서 탐색 범위를 절반씩 좁혀가며 데이터를 탐색하는 방식
> 

시간복잡도 : O(logN)

### 동작 방식

1. 배열의 중간 값(mid)을 비교
    1. 중간 값 == key :  검색을 종료
    2. 중간 값 > key : 중간 값의 왼쪽 배열 구간을 대상으로 탐색 
    3. 중간 값 < key : 중간 값의 오른쪽 배열 구간을 대상으로 탐색
2. key값을 찾거나, 탐색할 배열의 범위가 유효할 때까지 반복

ex)

![image](https://user-images.githubusercontent.com/72663337/193262985-852f3c7b-f64d-411c-826f-a6eb399c7a37.png)


위의 경우에서, mid 위치의 값(중간 값)은 key값보다 크므로, mid위치의 왼쪽 배열(색칠한 구간)을 대상으로 다시 탐색이 이루어진다.

### 단점

- 정렬된 데이터에 대해서만 탐색을 수행할 수 있다.
- 데이터에 중복된 값이 있는 경우, 원하는 결과를 얻지 못할 수 있다.

**반복문을 통하여 구현한 이진 탐색**

```java
/**
	 * @param arr 정렬된 배열
	 * @param number 탐색할 값
	 * @return 찾아낸 값의 인덱스(없는 경우 -1 return)
	 */
	private int binarySearch(int[] arr, int key) {

		int start = 0;
		int end = arr.length - 1;
		int mid;
		while (end >= start) {
			mid = (start + end) / 2;
			if(arr[mid] == key)
				return mid;
			else if (arr[mid] > key) {
				end = mid - 1;
			} else {
				start = mid + 1;
			}
		}
		return -1;
	}
```

→ 재귀 방식을 이용하여도 구현할 수 있지만, 반복문을 통한 방식이 더 효율적이다(stackoverflow 가능성 때문)

### Java 이진 탐색 라이브러리

Collections, Arrays의 binarySearch 함수를 이용할 수 있음

```java
Arrays.binarySearch(arr, key);
Collections.binarySearch(list, key);
```

key값의 인덱스 값을 return, 그렇지 않으면 -(insertion point)-1 을 리턴

ex)

```java
//int[] arr = {1,3,5,7,9};

Arrays.binarySearch(arr, 4);
//-(2)-1 = -3 return
```

4는 배열에 존재하지 않으므로, 4보다 큰 최초의 위치(insertion point)를 찾아 리턴

→ 이를 이용하여 lower_bound, upper_bound를 구현할 수 있음

### Reference

[https://codingdog.tistory.com/entry/java-arrays-binarysearch-함수를-알아봅시다](https://codingdog.tistory.com/entry/java-arrays-binarysearch-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%95%8C%EC%95%84%EB%B4%85%EC%8B%9C%EB%8B%A4)
