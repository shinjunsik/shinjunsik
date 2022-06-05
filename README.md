# 1. 리눅스 명령어 조사
## 1) top
 현재 OS의 상태를 나타내주는 CLI 어플리케이션이다.
 메모리 사용량, CPU 사용량 등을 나타내주며 주기적으로 업데이트해서 실시간에 근접한 내용을 보여준다. 위에는 전체 요약, 아래는 각 프로세스마다 구체적인 내용을 포함한다. 요약 영역은 전체 프로세스가 OS에 대해서 리소스를 어느 정도 차지하고 있는지를 알려준다.(시간, 유저, 로드 에버리지, 테스크, CPU, 메모리가 나타난다.)
 시간은 현재 시간이 가장 먼저 나타난다. 그다음은 OS가 얼마나 살아있는지를 그다음은 현재 접속 중인 유저 세션 수가 나타난다.
 로드 애버리지는 CPU Load의 이동 평균을 표시해 준다. 
 TASKS는 현재 프로세스들의 상태를 나타내준다. 그 아래는 CPU가 얼마나 어떻게 사용되고 있는지 그 사용률을 보여준다. 그다음엔 메모리 관련 영역이 나타난다. 첫 번째 줄은 RAM 그 다음 줄은 Swap 메모리가 나타난다. 

top용 커맨드
 k – kill process: k로 프로세스를 종료
 Sorting the process list: 디테일 영역에 대해서 원하는 값을 기준으로 정렬하는 방법 (M-> memory usage, P -> CPU usage, N -> process ID, T -> running time, R -> 오름차순, 내림차순)
 Showing a list of threads instead of processes: H를 누르면 쓰레드를 기준으로 보여주는 방식으로 변경
 Filtering through processes: o or O로 필터링 기능 사용 가능

## 2) ps
 현재 실행 중인 프로세스 목록과 상태를 보여준다. (정확한 옵션 사용 중요)
 사용법: $ps [option]
 단독으로 사용했을 땐 사용자와 관련된 프로세스를 출력 (보통 옵션들과 같이 사용)
 옵션
  -A: 모든 프로세스 출력
  a(BSD 계열): 터미널과 연관된 프로세스 출력
  -a: 세션 리더를 제외하고 터미널에 종속되지 않은 모든 프로세스를 출력
  -e: 커널 프로세스를 제외한 모든 프로세스를 출력
  -f: 풀 포맷으로 보여준다. (유닉스 스타일로 출력시켜주는 옵션)
  -l(sys V), l(BSD 계열): 긴 포맷으로 보여준다. (프로세스 정보를 길게 보여주는 옵션)
  -o: 출력 포맷을 지정하는 옵션
  -M: 64비트 프로세스들을 보여준다.
  -m: 프로세스들+ 커널 스레드들 보여줌
  -p: 특정 PID를 지정할 때 사용
  -r: 현재 실행 중인 프로세서를 보여준다.
  u(BSD 계열): 프로세스의 소유자를 기준으로 출력
  -u: 특정 사용자의 프로세스 정보를 확인할 때 사용
  x(BSD 계열): 터미널에 종속되지 않은 프로세스 출력
  -x: 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여준다. 

## 3) jobs
 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력된다. 각 작업에 번호가 붙어있다.
 사용법: $obs [옵션][작업 번호]
 옵션
  -l: 프로세스 그룹 ID를 state 필드 앞에 출력
  -n: 프로세스 그룹 중에 대표 프로세스 ID를 출력
  -p: 각 프로세스 ID에 대해 한 행씩 출력
  command: 지정한 명령어를 실행

 작업의 상태 값
  Running: 작업이 계속 진행 중임
  Done: 작업이 완료되어 0을 반환
  Done(code): 작업이 완료되었으며 0이 아닌 코드를 반환
  stopped:  작업이 일시 중단
  stopped(SIGTSTP): SIGTSTP 시그널이 작업을 일시 중단
  stopped(SIGSTOP): SIGSTOP 시그널이 작업을 일시 중단
  stopped(SIGTTIN): SIGTTIN 시그널이 작업을 일시 중단
  stopped(SIGTTOU):SIGTTOU 시그널이 작업을 일시 중단

## 4) kill
 대게 프로세스를 죽일 때 사용. 내부적으로는 프로세스에 시그널을 보내 원하는 작업을 수행하게 함
 사용법: $kill [options] <pid>
 
프로세스를 죽이는 방법
  $kill [pid]
  죽이려는 프로세스의 pid를 얻은 다음  kill 명령어의 인자로 넘긴다.

 사용자 지정 시그널 전송 방법
  $kill –s [signal] [pid]
  kill 명령어의 default 시그널은 TERM(15)이지만 –s로 다른 시그널을 보낼 수 있다.

 시그널을 보내는 다른 방법
  $kill –s KILL [pid]
  $kill –s SIGKILL [pid]
  
# 2. vim 에디터 매크로 사용방법 (q, @)
 q[NAME]을 치면 매크로가 시작한다. (아래에 “기록 중”이라는 문구가 뜬다.)
 이때 매크로로 지정하고 싶은 동작을 실행한다.
 매크로로 저장하고 싶은 동작을 다했으면 매크로가 끝났다는 뜻인 “q”를 입력한다.
 등록된 매크로를 실행하는 방법은 @[NAME]이다.
 [number]@[name]을 하면 number의 수만큼 매크로를 자동 실행한다.

<!---
shinjunsik/shinjunsik is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
