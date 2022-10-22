## Binary Tree

## 이진 트리의 특징

- 각 노드의 자식이 2개 이하
- 부모 노드의 왼쪽, 오른쪽 서브 트리도 이진 트리

이진 `탐색` 트리 → 이진 트리에 탐색을 위한 설정이 덧붙여진 것

# Binary Search Tree

`이진트리` + `연결 리스트`의 장점을 챙긴 트리

- 탐색의 효율을 높이고(이진 트리), 자료의 삽입-삭제(연결 리스트)를 가능하게 함
- 각 노드의 왼쪽 자식 < 부모 노드 < 오른쪽 자식 순으로 크기가 비교된다.

- 모든 노드는 유일한 키 값을 갖는다(중복 x)

![이진 탐색 트리-1](https://user-images.githubusercontent.com/72663337/197338650-da751b53-27ba-4223-9fa9-7d886336cf3f.png)


`이진 탐색 트리-1`

- 키 값들을 정렬된 상태(중위 순회하였을 때, 정렬된 결과를 얻을 수 있음)
    - 8 - 10 - 11 - 12 - 13 - 17

## 연산


### 검색

1. 루트 노드에서부터 시작
2. 현재 노드의 값 비교
    1. 현재 노드보다 검색 값이 더 클 때 → 오른쪽 서브 트리
    2. 현재 노드보다 검색 값이 작을 때 → 왼쪽 서브 트리
3. 위 과정을 현재 노드 값이 검색 값일 때까지 재귀적으로 수행

ex) 17 검색

### 삽입

1. 검색 과정 진행
2. 해당 위치에 삽입

ex) 이진 탐색 트리-1 → 9 삽입

- 결과

![이진 탐색 트리-2](https://user-images.githubusercontent.com/72663337/197338685-01967963-c2fd-4d8c-b68f-983f912e354f.png)


`이진 탐색 트리-2`

### 삭제

- 리프 노드를 삭제하는 경우
    
    → 그냥 삭제
    
- 자식 노드가 하나인 노드를 삭제하는 경우
    
    → 자식 노드를 삭제된 노드의 위치로 이동
    
- 자식 노드가 두 개인 노드를 삭제하는 경우
    
    → 오른쪽 서브 트리의 MIN or 왼쪽 서브 트리의 MAX 중 하나를 삭제할 노드로 이동
    

⇒ 이진 탐색 트리의 특징에 맞게 위치 조정하는 방식

ex1) 8 삭제

- 결과
    
    ![image](https://user-images.githubusercontent.com/72663337/197338707-44c97bb3-7439-4845-b421-eb350a73fa5e.png)

    노드 8의 자식 노드인 9의 위치 이동
    

ex2) 12 삭제

- 결과
    
    ![image](https://user-images.githubusercontent.com/72663337/197338729-0e5417b6-03d5-4bd3-93de-10fca10cb201.png)

    
    왼쪽 서브 트리의 MAX 노드 11로 대체
    
    (또는 오른쪽 서브 트리의 MIN값인 13으로도 대체 가능)
    

## 이진 탐색 트리의 시간복잡도

<aside>
💡 이진 탐색 트리의 시간복잡도는 O(log n)을 가진다.

</aside>

- 트리를 순회하며 탐색(또는 삭제, 추가)하므로, 시간복잡도는 트리의 높이에 비례하고,
    
    노드의 개수 n일 때
    
    트리의 높이 h = log2n 에 **비례하므로**, O(log n)의 시간복잡도가 된다.
    
    ### 이진 탐색 트리의 단점
    
    - 균형 트리일 때의 높이는 위의 결과와 같이 log2n이지만, 다음과 같이 편향 트리일 경우에는 다른 결과를 갖는다.
        
        ![image](https://user-images.githubusercontent.com/72663337/197338755-a02e4989-06ec-4093-b9fa-cab28c702f2d.png)

        
        이와 같은 최약의 경우에서는, 트리의 높이는 log2n이 아니라 n 이 되며, 시간복잡도 또한 연결 리스트와 동일한 O(n)을 갖는다.
        

### Q.

- 이진 탐색 트리의 시간복잡도
- 이진 탐색 트리인지 확인할 수 있는 방법
    
    → 이진 탐색 트리의 특징([중위 순회 방식으로 확인](https://www.notion.so/6b98d91f37114e53a434bdcae5aa8ddc) 등)
    

### Reference

[https://www.cs.usfca.edu/~galles/visualization/BST.html](https://www.cs.usfca.edu/~galles/visualization/BST.html)

[https://ha-young.github.io/2020/data-structrue/2020-09-22-자료구조-Tree에-대해-알아보자---1-트리,이진탐색트리/](https://ha-young.github.io/2020/data-structrue/2020-09-22-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-Tree%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90---1-%ED%8A%B8%EB%A6%AC,%EC%9D%B4%EC%A7%84%ED%83%90%EC%83%89%ED%8A%B8%EB%A6%AC/)
