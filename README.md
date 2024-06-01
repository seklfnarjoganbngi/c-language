# 20243130 신현성 과제

 # ___•  TOP___

  ##### top 명령어는 현재OS의 상태를 나타내주는 CLI어플리케이션이다.
  ##### CLI란 사용자가 텍스트로 명령어를 입력하면 텍스트로 결과를 화면에 출력해주는 인터페이스를 가진 컴퓨터를 의미한다.

  ##### OS는 운영체제라는뜻 

  ##### top의 상단은 요약영역이다 요약영역은 전체 프로세스가OS에 대해서 리소스를 어느정도 차지하고있는지 알려준다.
![image](https://github.com/lhh726/20233106-/assets/133843511/4f566a72-e31f-4cfa-b1fe-ba97f8403a24)

  ##### 요약영역에는 시간,유저,로드 에버리지,테스크,CPU,메모리가 나타난다.

  ##### 로드에버리지란 CPU Load의 이동평균을 의미한다 앞에서부터 1분,5분,15분에 대한 평균값이다.

  ##### CPU Load는 CPU가 수행하는 작업의 양이다 리눅스에서는 실행되거나 대기중인 프로세스의 평균이다. 싱글코어의 경우1.0의 값이 CPU를 100% 사용하고있다는 의미다.
  ##### 멀티코어라면 해당코어수만큼 *1 한 값이 CPU를 100%사용한다는 의미다.
  ##### 100%가 넘어간다면 CPU에서 처리하지 못하고 대기중인 프로세스가있다는것이다.
  
+ ### __Tasks__
  ##### 현재 프로세스들의 상태를 나타내주는 영역 
+ #### total
  ##### 전체 프로세스의 수

+ #### running
  ##### 실행중인 프로세스의 수

+ #### sleeping
  ##### 대기상태인 프로세스의 수

+ #### stopped
  ##### 종료된 프로세스의 수

+ #### zombies
  ##### 좀비상태인 프로세스 (좀비상태란 프로세스는 root Process로 부터 뿌리내린 자식process의 형식으로 트리구조를 형성하는데 부모 프로세스가 먼저 종료된다면 root process로 부터 닿을 수 없 는 Process가생기는데 이를 좀비프로세스라고 한다.)

+ ### __CPU__ 
  ##### Tasks 아래 %Cpu(s)라는 영역이 있다. 이 영역은 CPU가 어떻게 사용되고 있는지 그 사용율을 보여주는 영역이다. 모든 값의 총 합은 100% 이며 이를 퍼센테이지로 나누어서 보여준다. 

+ #### us  
  ##### 프로세스의 유저 영역에서의 CPU 사용률
+ #### sy  
  ##### 프로세스의 커널 영역에서의 CPU 사용률
+ #### ni  
  ##### 프로세스의 우선순위(priority) 설정에 사용하는 CPU 사용률
+ #### id  
  ##### 사용하고 있지 않는 비율
+ #### wa  
  ##### IO가 완료될때까지 기다리고 있는 CPU 비율
+ #### hi  
  ##### 하드웨어 인터럽트에 사용되는 CPU 사용률
+ #### si  
  ##### 소프트웨어 인터럽트에 사용되는 CPU 사용률
+ #### st  
  ##### CPU를 VM에서 사용하여 대기하는 CPU 비율

+ ### __메모리 사용량__

  ##### %Cpu(s) 영역 아래에 메모리와 관련된 영역이 있다. 첫번째 줄은 RAM의 메모리 영역으로 Mem이라 표시되어있는 부분이다. 그리고 아랫줄은 디스크를 메모리 처럼 이용하는 Swap 메모리 영역이다. 일반적으로 Mem의 사용량이 거의 가득 찼을때 Swap 메모리 영역을 사용한다. 이 영역은 디스크이기 때문에 RAM 메모리보다 속도가 많이 느린 단점을 가진다.

+ #### total  
  ##### 총 메모리 양
+ #### free  
  ##### 사용가능한 메모리 양
+ #### used 
  ##### 사용중인 메모리 양
  ##### * buff/cache에서 buff는 buffers의 약자이다. 이 값은 커널 버퍼에서 사용되는 메모리를 뜻한다. cache는 Disk의 페이지 캐시를 말한다. 즉, buff/cache는 IO와 관련되어 사용되는 버퍼에 사용되는 메모리를 말한다. 이 메모리가 있으므로써 IO에 상대적으로 빠른 속도를 가질 수 있다. avail Mem은 swap 메모리를 사용하지 않고 사용할 수 있는 메모리의 크기를 말한다.

+ ### ___디테일 영역___
![image](https://github.com/lhh726/20233106-/assets/133843511/b3f20f19-2556-4161-ad90-d223031ca6f4)

ㅤ
ㅤ
ㅤ
+ #### PID
  ##### PID는 프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값이다.
+ #### USER
  ##### 해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름이다.
+ #### PR & NI
+ #### PR  
  ##### 커널에 의해서 스케줄링되는 우선순위이다.
+ #### NI  
  ##### PR에 영향을 주는 nice라는 값이다.
+ #### VIRT, RES, SHR, %MEMVIRT, RES, SHR, %MEM
  ##### 해당 필드들은 프로세스의 메모리와 관련있다.
+ #### VIRT  
  ##### 프로세스가 소비하고 있는 총 메모리입니다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함한다.
+ #### RES  
  ##### RAM에서 사용중인 메모리의 크기를 나타낸다.
+ #### SHR 
  ##### 다른 프로세스와의 공유메모리(Shared Memory)를 나타낸다.
+ #### %MEM  
  ##### RAM에서 RES가 차지하는 비율을 나타낸다.
+ #### S 
  ##### 프로세스의 현재 상태를 나타낸다.
+ #### TIME+  
  ##### 프로세스가 사용한 토탈 CPU 시간
+ #### COMMAND  
  ##### 해당 프로세스를 실행한 커맨드를 나타낸다.
ㅤ
ㅤ

+ ### _top용 커맨드_
+ #### k - kill process
  ##### k키를 눌러서 사용, top를 통해 프로세스를 모니터링하며 프로세스를 종료할때 사용한다.
+ #### sorting the proccess list
##### 디테일 영역에서 원하는 값을 기분으로 정렬.
+ #### ‘M’  
##### 메모리 사용 순으로 정렬
+ #### ‘P’  
##### CPU 사용 순으로 정렬
+ #### ‘N’ 
##### 프로세스 ID순으로 정렬
+ #### ‘T’ 
##### 러닝타임 순으로 정렬
+ #### ‘R’ 
##### 오름차순과 내림차순을 토글 변경
ㅤ
ㅤ

![image](https://github.com/lhh726/20233106-/assets/133843511/3378c1a7-7782-45a0-b7cc-92d8515c071d)
###### M커맨드를 사용하여 메모리 사용순으로 정렬한 모습


+ #### Showing a list of threads instead of process
##### top는 기본적으로 프로세스를 기본으로하여 정보를 보여준다.
##### H를 누르면 쓰레드를 기준으로 보여주는 방식으로 변경된다.
##### task영역과 디테일 영역이 변경된다.
![image](https://github.com/lhh726/20233106-/assets/133843511/c05a8514-ac89-4e9b-949d-915b35facbcf)
###### H커맨드를 사용하여 task영역과 디테일 영역이 바뀐모습
ㅤ
ㅤ
ㅤ

+ #### Filtering through processes
##### o또는O를 눌러서 프로세스를 필터링해준다.
##### ex)o누른후 COMMAND=JAVA를 입력시 커맨드에 자바가 포함되는 프로세스만 확인 할 수 있다.
![image](https://github.com/lhh726/20233106-/assets/133843511/23f0d1a6-d8a5-4efd-8f41-2961893995a2)
###### 예시의 커맨드를 사용한 모습, 커맨드에 자바가 포함된 프로세스가 존재하지 않아 표시되지 않은 모습이다.

# • ___PS___

#### _ps_  
##### 현재 실행중인 프로세스 목록과 상태를 보여준다.
![image](https://github.com/lhh726/20233106-/assets/133843511/7bdf7757-7f2b-41cd-bd49-8764a4ca3332)
ㅤ
ㅤ

#### 유닉스
##### system V : - 사용
##### system BSD : - 사용 X 
#####  system GNU : -- 두개 사용
##### 프로세스의 상태를 출력할려면 정확한 옵션의 사용이 중요하다!

#### ps 사용법: $ ps [option]

### ___option___
+ #### -A  
##### 모든 프로세스 출력
+ #### a (BSD계열)  
#####  터미널과 연관된 프로세스 출력. 보통 x옵션과 연계하여 모든 프로세스 출력할때 사용
+ #### -a  
##### 세션 리더(일반적으로 로그인 셀)을 제외하고 터미널에 종속되지 않은 모든 프로세스 출력
+ #### -e  
##### 커널 프로세스를 제외한 모든 프로세스 출력 
+ #### -f  
##### 풀 포맷으로 보여줌. 유닉스 스타일로 출력 UID, PID, PPID등이 표시
+ #### -l(sysV) 
##### 긴 포맷으로 보여줌. 프로세스의 정보를 길게 보여주는 옵션 우선순위와 관련 PRL와 NI값 확인 가능
+ #### l (BSD계열) : (위와 동문) 
+ #### -M 
##### 64비트 프로세스들을 보여준다.
+ #### -m 
##### 프로세스들 뿐만 아니라커널 스레드들도 보여준다.
+ #### -p
##### 특정 PID를 지정할 때 사용한다.
+ #### -r 
##### 현재 실행 중인 프로세서를 보여준다.
+ #### u (BSD계열) 
##### 프로세스의 소유자를 기준으로 출력한다. (ps ax만 하면 USER 기준의 정보가 안뜬다. 따라서 aux 이렇게 같이 보통 써준다)
+ #### -u
##### 특정 사용자의 프로세스 정보를 확인할 때 사용한다. 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력한다.
+ #### x (BSD계열) 
##### 데몬 프로세스처럼 터미널에 종속되지 않는 프로세스를 출력한다. 보통 a옵션과 결합하여 모든 프로세스를 출력할 때 사용한다.
+ #### -x  
##### 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여준다. 유닉스 시스템은 사용자가 로그아웃 한 후에도 임의의 프로세서가 계속 동작할게 할 수 있다. 그러면 그 프로세서는 자신을 실행시킨 셸이 없어도 계속 자신의 일을 수행하는데 이러한 프로세스는 일반적인 ps명령으로 확인 할 수 없다. 이때 -x 옵션을 사용하면 자신의 터미널에 없는 프로세서들을 확인 할 수 있다.

+ #### ex) ps -ef'프로세스명'ㅤ//ㅤㅤps aux | grep '프로세스명'
ㅤ


+ ### __ps항목__
```
• USER
BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름
• UID
SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름
• PID
프로세스의 식별번호
• PPID
부모 프로세스 ID
• %CPU
CPU사용 비율의 추정치(BSD)
• %MEM
메모리 사용 비율의 추정치(BSD)
• VSZ
K단위 또는 페이지 단ㄴ위의 가상메모리 사용량
• RSS
실제 메모리 사용량
• TTY
프로세스와 연결된 터미널
• S,STAT
현재 프로세스의 상태 코드
• OMMAND
프로세스의 실행 명령행
• STIME
프로세스가 시작된 시간 혹은 날짜
• C,CP
짧은 기간 동안의 CPU사용률
• F
프로세스의 플래그
• PRI
실제 실행 우선순위
• NI
nice우선순위 번호
 ```

### __ps명령어 사용예시__
```
$ps ax
$ps aux
$ps aux | grep apache
$ps -ef | more
$ps-el | head
$ps -fp[PID]
$ps-U root -u root
$ps -t pts/18
$ps -e -o pid,ppid,uname,pcpu,pmem,comm,tty, | head
$ps -p 1222 -o comm=: pid가 1222인프로세스의 이름을 출력해라
$ps -C httpd -o pid= : 이름이 httpd인 프로세스들의 pid를 출력해라
```
ㅤ
ㅤ
ㅤ
ㅤ
# ___• KILL___
##### 프로세스를 지정하고 시그널을 보내서 제어하는 명령어이다. 리눅스 환경에서 응용프로그램이나 프로세스가 멈출 때 해당 프로세스를 종료하기위해 사용한다.

##### 주로 프로세스 종료의 용도로 이용된다.

##### $ kill [options] <pid> 의 구문을 사용한다

##### 여기서 PID번호를 찾으려면 ps명령어를 사용해야한다

+ ### _options_

+ #### -9 
##### 프로세스 아이디를 직접 지정하여 종료시 사용된다.

+ #### -l
 ##### 신호로 사용할 수 있는 신호이름들을 보여준다.

+ #### 1(HUP) 
##### 프로세스를 다시 로드한다.

+ #### 9(KILL) 
##### 프로세스를 제거한다.

+ #### 15(TERM)  
##### 프로세스를 정상적으로 중지한다.
 ㅤ
ㅤ
 ㅤ
ㅤ
 
# ___• JOBS___
##### jobs명령어는 작업의 상태를 표시하는 명령어이다.
##### 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있다.
 ㅤ
ㅤ
 ㅤ
+ ### __jobs로 출력되는 백그라운드 작업의 상태값__

 ```
• Running
작업이 계속진행중일때
• Done
작업이 완료되어 0을 반환한다
• Done(code)
작업이 종료되었으며 0이 아닌 코드를 반환한다
• Stopped
작업이 일시 중단되었다
• Stopped(SIGTSTP)
SIGTSTP 신호가 작업을 일시중단했다
• Stopped(SIGSTOP)
SIGSTOP 신호가 작업을 일시중단했다
```
ㅤ
 ㅤ
ㅤ
 + ### __옵션__
|ㅤ-l |   -n   |  -p   |   command  |
| ----------------------------------------| ------------------------------------------| --------------------------------------| ------------------------|
|프로세스 그룹 ID를 state 필드 앞에 출력한다 | 프로세스 그룹 중에 대표 프로세스 ID를 출력한다 | 각 프로세스 ID에 대해 한 행씩 출력한다 | 지정한 명령어를 실행한다|
