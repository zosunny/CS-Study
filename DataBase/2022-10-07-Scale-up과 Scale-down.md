<aside>
💡 인프라 확장을 위한 2가지 방법 Scale up / Scale out

</aside>

서버 운영시 이용자 증가 또는 사업 확장으로 인해 많은 서버 용량과 성능 필요.

이때, Scale up과 Scale out으로 인프라 확장 문제 해결

## 1. Scale up

<aside>
💡 기존 서버의 사양 업그레이드해 시스템 확장

</aside>

- CPU(프로세서)나 RAM(메모리)등을 추가 or 고성능의 부품, 서버로 교환
- `SMP(대칭형 멀티 프로세서)`에 대해 CPU등의 프로세서를 추가하거나 고성능 모델로 교환
    - `SMP(대칭형 멀티 프로세서)`
        
        *대칭형 다중 처리, 두개 또는 그 이상의 프로세서가 한 개의 공유된 메모리를 사용하는 다중 프로세서 컴퓨터 아키텍처*
        
        *현재 사용되는 대부분의 다중 프로세서 시스템은 SMP 아키텍처 따르고 있음.*
        
- 하나의 서버 사양 업그레이드 → `수직 스케일` 이라고도 불림

## 2. Scale out

<aside>
💡 서버를 여러 대 추가해 시스템 확장

</aside>

- 각 서버에 걸리는 부하 균등하게 해주는 `‘로드밸런싱’` 필수적으로 동반되어야 함
    - `로드밸런싱`
        - 컴퓨터 네트워크 기술의 일종
        - 2개 이상의 중앙처리장치/저장장치와 같은 컴퓨터 자원들에게 작업(Work) 즉, 부하(Load)를 나누는 것
- 여러 대의 서버로 나눠 시스템 확장 → `수평 스케일` 이라고도 불림

## 3. Scale up VS Scale out

![스크린샷 2022-10-02 오후 4.13.22.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f2c51636-bd9c-48a4-b973-a75cd27a75f9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-10-02_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4.13.22.png)

![스크린샷 2022-10-02 오후 4.20.55.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/56ee756f-394d-43c9-ac9c-8a9e7ff5a722/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-10-02_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4.20.55.png)

- `데이터 정합성`
    - 데이터가 서로 모순 없이 일관되게 일치해야 함
    - 중복 데이터를 많이 사용하면 데이터끼리 정합성을 맞추기 어려움
    - 비정규형 사용해 anomaly(이상현상)가 발생하면 정합성 깨짐
    - 어떤 데이터의 경우 정합성은 이상이 없으나, `데이터 무결성`이 훼손될 수 있음
        - `데이터 무결성`
            - 데이터의 값이 정확한 상태
            - 개체 무결성 / 참조 무결성 / 도메인 무결성 / 업무 무결성 존재

## Reference

[https://dev-coco.tistory.com/143](https://dev-coco.tistory.com/143)

[https://pakpark.tistory.com/46](https://pakpark.tistory.com/46)

[https://blog.naver.com/PostView.naver?blogId=remocon33&logNo=222479119313&parentCategoryNo=53&categoryNo=&viewDate=&isShowPopularPosts=true&from=search](https://blog.naver.com/PostView.naver?blogId=remocon33&logNo=222479119313&parentCategoryNo=53&categoryNo=&viewDate=&isShowPopularPosts=true&from=search)
