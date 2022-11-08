# Process

---

<aside>
  
💡 운영체제로부터 자원을 할당받는 **자원의 단위**

</aside>

- 독립된 메모리 공간을 할당받아 프로그램을 실행하는 **작업**을 수행하는 하나의 인스턴스

![Process의 메모리 영역](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c7f77ceb-d6e4-49b4-9ab7-afe512195829/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221108%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221108T051434Z&X-Amz-Expires=86400&X-Amz-Signature=968db8a113c0db83b299d4e3cc2e00dba2d1e975cb5ee35fd4f9a58b2e9408fe&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

`Process의 메모리 영역([https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html))`


- 각 프로세스 메모리들은 다른 프로세스의 메모리와 분리되어 접근할 수 없다.
    
    → 프로세스 간 통신 (IPC : Inter-Process Communication)을 사용하면 접근 가능
    

# Thread

---

<aside>
💡 할당받은 자원을 이용하는 **실행 흐름의 단위**

</aside>

- 프로세스에서의 **특정 수행 경로의 흐름**을 의미 → 사실상 프로세스에 포함되어 있는 단위라고 볼 수 있음
- 하나의 프로세스는 최소 하나의 스레드를 갖고 있음(main thread)

![Thread의 메모리 영역](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91b0d4f8-0e0c-45f2-96ad-8f897a65efb7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221108%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221108T051514Z&X-Amz-Expires=86400&X-Amz-Signature=2add06fc27afa6cddbc38399655c16ae6ab721f111e73cff209d4eb76a3f5274&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

`Thread의 메모리 영역([https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html))`

- stack 영역을 제외하고는 메모리를 공유하여 사용하기 때문에, 각 스레드의 실행이 서로에게 영향을 끼침

## multi tasking(process) vs multi thread

- **multi tasking**
    - 하나의 os 안에서 여러 프로세스가 병렬적으로 실행
    - (+) : 각 프로세스는 독립적으로 동작하므로, 하나에 문제가 생기더라도 다른 프로세스들에게는 영향을 끼치지 않음
    - (-) : **context switching** 과정에서 오버헤드가 발생할 수 있음
- **multi thread**
    - 하나의 프로세스 안에서 하나의 작업을 여러 스레드를 사용하여 동시에 처리
    - (+)
        
        stack영역을 제외하고는 메모리 공유가 일어나기에 자원의 효율적인 이용이 가능하고
        
        스레드 간 데이터의 전달이 용이해 통신의 부담이 덜하며
        
        응답 시간이 빠르다.
        
    - (-)
        
        자원을 공유하기에 **동기화 문제**가 발생할 수 있다.
        
        디버깅이 까다롭다.
        

⇒ 💩 보통은 멀티 프로세스 대신 멀티 스레드가 사용된다. (하나의 프로그램 안에서 여러 동작-작업을 수행)

프로세스 간의 context switching의 오버헤드가 제일 큰 이유

> ❓ **context switching**
프로세스의 전환이 일어날 때, 이전에 동작했던 프로세스의 상태(context)를 보관하고, 다음 순서로 동작하는 프로세스를 위해 보관된 context를 복구하는 작업
> 

[Thread-safe] 

- 스레드들이 같은 데이터에 접근하므로써 생기는 동시성 문제를 해결하기 위함
- 여러 스레드에서 특정 데이터에 동시 접근하여 사용하더라도 안전하고 정확하게 동작하도록 함

### Reference

[https://velog.io/@raejoonee/프로세스와-스레드의-차이](https://velog.io/@raejoonee/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C%EC%9D%98-%EC%B0%A8%EC%9D%B4)
