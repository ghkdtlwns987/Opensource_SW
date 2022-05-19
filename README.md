# 20184327 황시준 오픈소스 SW 과제
<img src="https://user-images.githubusercontent.com/54488922/168478163-dad1a247-58cf-4e5f-9870-4dd75ae66bfd.png" width="50%" height="50%"/>

## 리눅스 명령어
|명령어|설명|예시|링크|
|----|-----|---|---|
|top|실시간으로 업데이트 되는 메모리 사용량, CPU 사용량 등을 보여줌.|$ top|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_top)|
|ps|현재 실행중인 프로세스의 목록을 보는 명령어이다.|$ ps -ef|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ps)|
|jobs|현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되는 명령어이다.|$ jobs|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_jobs)|
|kill|프로세스에 시그널을 보내는 명령어이다.|$ kill [process name]|[바로가기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%A4%91%EC%A7%80_kill)|

### top 
#### 설명
- 유닉스계열 시스템에서 프로세스 목록을 CPU 사용률이 높은 것부터 보여주는 소프트웨어
- 첫 줄의 결과는 uptime 명령어와 동일하다.

![top 설명](https://user-images.githubusercontent.com/54488922/169214594-9906287d-fc58-40c9-9e5b-bdb70952054e.png)

[모든 내용 보기](https://man7.org/linux/man-pages/man1/top.1.html)

### ps [ps -ef] [ps aux]
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
- ps -ef : PID와 PPID 등 확인 가능
- ps aux : CPU, MEM 사용률, 프로세스 상태 코드 등 확인 가능

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

[모든 내용 보기](https://man7.org/linux/man-pages/man1/jobs.1p.html)


### kill [kill -9 [PID]] [kill [PID]]
- 프로세스에 시그널을 보내는 명령어로 주로 프로세스를 강제 종료할때 사용된다. 
- kill -9 [PID] 
#### Options
|옵션 혹은 SIGNUM|설명|
|---|---|
|-l|signal 종류 출력(여기서 9번의 SIGKILL 이다.)|

![kill 내용](https://user-images.githubusercontent.com/54488922/169214570-6b502c87-aa37-474b-ada5-54c7fc84f5f5.png)

[모든 내용 보기](https://man7.org/linux/man-pages/man2/kill.2.html)
