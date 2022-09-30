### 스케줄링

- 다중 프로그래밍(여러 프로그램을 동시에 처리하는 방식)에서 사용
- 프로그램(프로세스)은 맡은 작업을 수행하기 위해 CPU를 할당받아야 함
    
     → 어떤 프로세스에 한정된 CPU를 할당하여 처리할 것인지 결정하는 과정
    

### 프로세스들을 실행시키기 위한 Queue 3가지

> Job Queue : 현재 시스템 내의 모든 프로세스
> 
> 
> secondary storage에 형성되어 있는 큐
> 

> Ready Queue : 현재 메모리 내에 로드되어 있으면서, **CPU를 할당받아** **실행되기를 기다리는** 프로세스
> 

> Device Queue : device I/O 작업을 대기하는 프로세스
> 

⇒ 어떤 프로세스들을 각각의 Queue에 넣고 빼낼 지를 스케줄링하는 스케줄러 또한 존재

![image](https://user-images.githubusercontent.com/72663337/193262311-7b71e785-2587-44c3-8b9a-217d8e895167.png)

`Process State`

## 장기 스케줄러(Job scheduler)

CPU 메모리 크기는 한정되어 있으므로, 많은 프로세스들이 한꺼번에 메모리에 오르게 될 때, 이들을 대용량 저장 장치(보통은 디스크)에 임시로 저장한다.

임시 저장된 프로세스들 중 메인 메모리가 할당되어 ready queue로 보내질 프로세스를 결정하는 역할을 한다.

- 메모리 - 디스크 사이의 스케줄링 담당
- new → ready(in memory)
- degree of multiprogramming 제어(실행 중인 프로세스의 수 제어)

## 단기 스케줄러(CPU scheduler)

Ready Queue의 프로세스들 중 어느 프로세스를 running시킬지 결정하는 역할을 한다.

- 메모리와 CPU 사이의 스케줄링을 담당
- 프로세스에 CPU 할당(dispatch)
- ready → running

## 중기 스케줄러(Swapper)

여유 공간 확보를 위해서 메모리의 프로세스들을 **디스크**로 쫓아냄(swapping)

장기 스케줄러와 더불어, 너무 많은 프로세스들이 메모리에 올라가는 것을 조절하는 역할을 한다.

memory를 deallocate

- ready → suspended

## CPU Scheduler(단기 스케줄러)

> Ready Queue의 프로세스들을 대상으로 스케줄링
> 

### 스케줄링의 평가 기준 척도

- CPU 사용률(CPU Utilization)
    
    전체 시스템 시간 중 CPU가 작업을 처리하는 시간의 비율(대기 시간이 길수록 사용률 하락)
    
- 처리량(Throughput)
    
    CPU가 단위 시간당 처리하는 프로세스의 개수
    
- **대기 시간(Waiting Time)**
    
    프로세스가 ready queue 내에서 대기하는 시간의 총 합
    
- **응답 시간(Response Time)**
    
    요청 후 응답이 오기 시작할 때까지의 시간
    
    프로세스 실행 시각(running) - 처음 생성된 시각(new)
    
- **반환 시간(Turnaroung Time)**
    
    프로세스 시작부터 끝날 때까지 소요되는 시간
    
    종료 시각(terminated) - 처음 생성된 시각(new)
    

→ 보통 대기 시간, 응답 시간, 반환 시간을 기준으로 스케줄링의 효율성이 평가되는 경우가 많다.(나머지 기준들은 컴퓨터 성능에 의한 경우가 많고, 측정하기 어렵기 때문)

### 스케줄링 알고리즘

1. **비선점형(Non-preemptive) 스케줄링**
    
    <aside>
    👽 CPU가 프로세스에 할당되면, 해당 프로세스의 작업이 완료될 때까지(CPU burst) CPU를 반환하지 않는다.
    
    </aside>
    
    → 한 프로세스가 CPU를 점유하고 있을 때, 이를 빼앗아 재할당할 수 없다.
    
- **`FCFS(First Come First Served)`**
    - 먼저 온 **순서대로** 처리
    
    문제점
    
    - convoy effect
        
        소요 시간이 긴 프로세스가 먼저 도달했을 때, 대기 시간이 길어져 전체적인 작업의 효율성을 낮추는 현상이 발생함
        
- **`SJF(Shortest Job First)`**
    - CPU burst time이 짧은 프로세스에게 CPU가 먼저 할당
    
    문제점
    
    - 기아 현상(starvation)
        
        최악의 경우, 사용 시간이 긴 프로세스는 CPU를 할당받는 우선순위가 계속 밀리게 됨.
        
    - convoy effect

1. **선점형(Preemptive) 스케줄링**
    
    <aside>
    👽 어떤 프로세스에 CPU가 할당되어 실행 중이더라도, 이를 빼앗아 재할당할 수 있는 방식
    
    </aside>
    
    → 잦은 문맥 교환(프로세스의 정보를 토대로 CPU를 재할당하는 과정)으로 오버헤드가 많이 발생할 수 있다.
    
    - `**SRTF(Shortest Remaining Time First)**`
        - SJF의 선점형 알고리즘 버전, 새로운 프로세스가 도착할 때마다 남은 CPU burst time이 가장 짧은 프로세스를 기준으로 CPU가 재할당
        
        문제점
        
        - 기아 현상(starvation)
2. **그 외의 방식**
    - `**Priority Scheduling**`
        - **우선순위**가 가장 높은 프로세스에게 CPU 할당
        - 선점형, 비선점형 두 개의 방식으로 스케줄링 가능
        
        문제점
        
        - 기아 현상(starvation)
            
            →  **aging**(프로세스의 대기 시간이 길어질 경우에, 우선순위를 높여주는 방식)으로 기아 현상을 해결할 수 있음
            
    - `**Round Robin**`
        - 동일한 크기의 **할당 시간**(time quantum)동안 CPU가 할당
        - 할당 시간이 지나면 프로세스는 CPU를 빼앗기며, ready queue의 뒤로 들어가 대기
        - 모든 프로세스들이 공정하게 시간을 할당받으며, 프로세스의 대기 시간을 예상하기 쉬움
        - 응답 시간(Response Time) 면에서 상대적으로 이득을 본다.
        
        주의점
        
        - 설정한 할당 시간(time quantum)이 너무 크면 FCFS와 같아지고, 너무 작아지면 잦은 **문맥 교환(context switching)** 으로 인한 오버헤드가 발생한다.
            
            → 적절한 `time quantum`을 설정하는 것이 중요하다.
            

## Question

- 어떤 기준으로 CPU 스케줄링을 선택해야 하는가?(평가 기준)
- 선점형 스케줄링 vs 비선점형 스케줄링

### Reference

[https://velog.io/@yuiopre98/cs-면접-1주차-스케줄러](https://velog.io/@yuiopre98/cs-%EB%A9%B4%EC%A0%91-1%EC%A3%BC%EC%B0%A8-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC)

[https://itwiki.kr/w/프로세스_상태](https://itwiki.kr/w/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%83%81%ED%83%9C)
