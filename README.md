# 20184327 황시준 오픈소스 SW 과제

## 리눅스 명령어
| 명령어 |설명|예시|링크|
|----|-----|---|---|
|```top```|실시간으로 업데이트 되는 메모리 사용량, CPU 사용량 등을 보여줌.|```$ top```|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_top)|
|```ps```|현재 실행중인 프로세스의 목록을 보는 명령어이다.|```$ ps -ef```|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ps)|
|```jobs```|현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되는 명령어이다.|```$ jobs```|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_jobs)|
|```kill```|프로세스에 시그널을 보내는 명령어이다.|```$ kill [process name]```|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%A4%91%EC%A7%80_kill)|

### top 
#### 설명
- 유닉스계열 시스템에서 프로세스 목록을 CPU 사용률이 높은 것부터 보여주는 소프트웨어

![top 설명](https://user-images.githubusercontent.com/54488922/169214594-9906287d-fc58-40c9-9e5b-bdb70952054e.png)

top 명령어는 줄 순서대로 표현한다고 보면 된다.
1. 로드 에버리지 (Load Average)
2. Tasks
3. CPU 사용량
4. 메모리 사용량
5. 디테일 영역


[모든 내용 보기](https://man7.org/linux/man-pages/man1/top.1.html)

### ps [```ps -ef```] [```ps aux```]
#### 설명
- Process status 의 약자로 현재 실행중인 프로세스 목록을 보는 명령어이다. 
- ps -ef , ps aux 를 많이 사용한다. 
#### Options
※ -u 옵션과 u 옵션과 같이, 옵션에 (-) 를 붙인것과 붙이지 않은 것은 서로 다르다!
|옵션|설명|
|---|---|
|-e|실행중인 모든 프로세스 정보 출력|
|-f|프로세스에 대한 자세한 정보 출력|
|-p|pid로 지정한 프로세스 정보 출력|
|-u|특정 사용자에 대한 모든 프로세스 정보 출력|
|u|프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세 정보 출력|
|a|터미널에서 실행한 프로세스의 정보를 출력|
|x|실행중인 프로세스의 정보를 출력|

#### 자주쓰는 옵션
- ```ps -ef : PID와 PPID 등 확인 가능```
- ```ps aux : CPU, MEM 사용률, 프로세스 상태 코드 등 확인 가능```

[모든 내용 보기](https://man7.org/linux/man-pages/man1/ps.1.html)

### jobs 
- 백그라운드로 실행되는 작업목록(작업번호, 상태, 명령어)을 보여주는 리눅스 명령어
- 여기서 작업번호는 PID와는 달리, 별도로 부여되는 백그라운드 작업목록 상의 번호이다.
- 작업목록은 현재 쉘 세션에 딸린 것이며, 다른 세션과는 독립적이다.
- 현재 쉘 프로세스(bash)의 자식 백그라운드 프로세스들을 보여준다고 할 수 있다.
- 리눅스 kill 명령어 뒤에 %작업번호를 입력하여 종료시킬 수 있다.

#### Options
|옵션|설명|
|---|---|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|

#### ※jobs 로 알 수 있는 세션의 상태 값
|상태|설명|
|---|---|
|Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done|작업이 완료되어 0을 반환하고 종료 했음을 의미|
|Done(code)|작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|

![jobs](https://user-images.githubusercontent.com/54488922/169215267-de3ad049-73df-4225-957e-d3759b95c4d4.png)
위 그림을 구면 프로세스가 멈춰있거나 실행중인 경우를 출력해 준다. 
jobs 는 이렇게 background 프로세스를 Foreground 로 전환하거나 다시 background 로 전환시킬 수 있다. 


[모든 내용 보기](https://man7.org/linux/man-pages/man1/jobs.1p.html)  



### kill [```kill -9 [PID]```] [```kill [PID]```]
- 프로세스에 시그널을 보내는 명령어로 주로 프로세스를 강제 종료할때 사용된다. 
- ```kill -9 [PID]``` 
#### Options
|옵션 혹은 SIGNUM|설명|
|---|---|
|-l|signal 종류 출력(여기서 9번의 SIGKILL 이다.)|

![kill 내용](https://user-images.githubusercontent.com/54488922/169214570-6b502c87-aa37-474b-ada5-54c7fc84f5f5.png)

[모든 내용 보기](https://man7.org/linux/man-pages/man2/kill.2.html)

  
    
## vim 매크로 사용법
### (1) 기본적인 매크로 사용방법
1. ```커맨드 모드(esc 누른 상태)``` 진입
2. ```'q'```를 누르고 ```a~z``` 사이 문자로 매크로(recording) 시작 **(여기서 입력한 알파벳이 매크로 이름이 된다.)**
3. 매크로를 사용하려면 커맨드 모드에서 ```@+a~z``` 입력

### (2) 매크로 재생하는 법
1. ```커맨드 모드(esc 누른 상태)``` 진입
2. ```@a```라고 누르면 매크로 ```a```가 재생된다.
3. ```@@```를 누르면 가장 ```최근에 재생한 매크로```가 실행

### (3) 자주 사용하는 매크로 파일로 저장 방법
1. ~/.vimrc 를 연다
2. ``` let @a = '매크로로 동작시킬 문자열'   // 여기서 이름은 a로 지정한다는 뜻이다. (@a) ```

### 예시
![vim 매크로 1](https://user-images.githubusercontent.com/54488922/169224495-a48e7d41-1c91-4d42-83b6-f582e085fd7f.png)  
위 상태를  

![vim 매크로 5](https://user-images.githubusercontent.com/54488922/169224510-b7d39810-f48d-47c9-977e-1c04a01d621f.png)  
위 상태로 매크로를 통해 바꿔보고자 한다.  
  
먼저 ```esc```를 누르고 ```qe``` 를 누른다 (매크로 이름을 e로 설정할 거기 때문)  
그럼 아래 상태처럼 된다.  
![vim 매크로 2](https://user-images.githubusercontent.com/54488922/169224916-4af582d6-afa6-4a4d-9b38-d00341ff83c6.png)    

이후 ```ww``` 를 눌러 다음 학번으로 이동한다. 그럼 커서가 다음과 같이 위치할 것이다.   
![vim 매크로 3](https://user-images.githubusercontent.com/54488922/169224502-bcd14683-df67-4229-8fab-3a6e13bd518c.png)    

커서가 위처럼 위치했으면 13x 로 공백을 포함한 문자를 제거한 후 ```www``` 를 입력해     
위와같이 커서를 위치시키로 매크로를 **저장**하기 위해 ```q```를 입력해 매크로를 저장한다.    
![vim 매크로 4](https://user-images.githubusercontent.com/54488922/169224505-79165488-ff76-4684-9fda-1b3ef4e950f7.png)    

위 작업을 반복하기 위해 ```@@``` 나 ```@e``` 를 계속해서 입력해주면 아래와 같이 된다.    
![vim 매크로 5](https://user-images.githubusercontent.com/54488922/169224510-b7d39810-f48d-47c9-977e-1c04a01d621f.png)    

