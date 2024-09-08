## 🧐 Additional Informations

### 스택(stack)

스택은 LIFO (Last In, First Out) 구조를 가진 자료구조로, 가장 마지막에 삽입된 데이터가 가장 먼저 삭제되는 구조입니다.

<p align="center">
<img width="60%" alt="stack" src="https://github.com/user-attachments/assets/a94981a8-948a-4877-aa8e-04431f30cd9d">
</p>

데이터를 삽입하는 push 연산과 데이터를 삭제하는 pop 연산을 제공합니다. <br />
데이터는 항상 스택의 가장 상단에 추가되거나 제거됩니다.

###### usage

함수 호출, 괄호 짝 맞추기, 후위 표기법 계산 등의 상황에서 사용됩니다. <br />
함수 호출에서는 스택을 사용하여 함수의 매개변수, 지역 변수, 반환 주소를 관리하며, 이를 통해 함수가 실행되는 동안의 상태를 유지합니다.

스택은 깊이 우선 탐색(DFS) 알고리즘, 역순 문자열 생성, 실행 취소 기능 등에서 사용됩니다.

재귀적인 함수, 알고리즘, 웹 브라우저 방문 기록 등

<br />

### 큐 (queue)

큐는 FIFO (First In, First Out) 구조를 가지며, 가장 먼저 삽입된 데이터가 가장 먼저 삭제되는 구조입니다.

<p align="center">
<img width="60%" alt="queue" src="https://github.com/user-attachments/assets/9b79882f-453e-4350-ad2c-d41a07bbc335">
</p>

큐는 데이터를 삽입하는 enqueue 연산과 데이터를 삭제하는 dequeue 연산을 제공합니다. <br />
데이터는 큐의 뒤쪽에 추가되고, 앞쪽에서 제거됩니다.

###### usage

큐는 프린터 대기열, 버퍼 관리, 스케줄링 알고리즘 등의 상황에서 사용되며, 데이터가 순차적으로 처리되어야 하는 경우에 적합합니다.

큐는 너비 우선 탐색(BFS) 알고리즘, 작업 스케줄링, 캐시 구현 등에서 사용됩니다.

CPU 작업을 기다리는 프로세스, 스레드 행렬, 네트워크 접속을 기다리는 행렬, 너비 우선 탐색, 캐시 등

<br />
<br />
<hr />

References.

- [선형 자료 구조와 비선형 자료 구조](https://velog.io/@55555-jyeon/data-structure)
- [스택(Stack) 과 큐(Queue)](https://velog.io/@moonblue/%EC%8A%A4%ED%83%9DStack-%EA%B3%BC-%ED%81%90Queue)
