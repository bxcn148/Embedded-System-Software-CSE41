Download link :https://programming.engineering/product/embedded-system-software-cse4116-%ea%b3%bc%ec%a0%9c-2/


# Embedded-System-Software-CSE41
Embedded System Software [CSE41
목표

타이머 디바이스 드라이버 및 관련 테스트 응용 프로그램을 개발한다.

구현

2.1. 응용프로그램

사용자로부터 타이머 디바이스 구동 옵션을 받아 ioctl 을 통하여 타이머 디바이스 드라이버에 전달하고 ioctl 을 통해 타이머 디바이스를 구동한다. (두 개의 ioctl 명령어 사용)

2.2. 타이머디바이스드라이버

디바이스 드라이버 (fpga_fnd, fpga_led, fpga_dot, fpga_text_lcd, fnd_push_switch)와 타이머 기능을 포함한 하나의 module 을 구현한다.

세부기능

3.1. 응용프로그램

사용자로부터 타이머 디바이스 구동 옵션을 받아 ioctl 을 통하여 타이머 디바이스 드라이버에 전달하고 ioctl 을 통해 타이머 디바이스를 구동한다. 이 때 두 개의 ioctl 명령어를 사용한다.

Ex) ioctl(fd, SET_OPTION, …) / ioctl(fd, COMMAND, …)

실행예시는다음과같다.

./app TIMER_INTERVAL[1-100] TIMER_CNT[1-100] TIMER_INIT[0001-8000]

TIMER_INTERVAL: HZ 값 1~100 (0.1~10초)

TIMER_CNT: 디바이스출력변경횟수 (1~200)

TIMER_INIT: FND 에출력되는초기문양과위치 (0001~8000)

단, 4 자리중한자리만 1~8 숫자가입력되도록설정한다. 예를 들어, 0040 이라면 왼쪽에서세번째자리에 “4”를출력한다.

TIMER_CNT 및 TIMER_INIT 에대한사항은 3.2 타이머디바이스드라이버에서 상세히설명한다. 응용프로그램에올바른값이들어갈수있도록예외처리한다.

프로그램을 위와 같이 실행하면 ioctl : SET_OPTION 을 통해 타이머 디바이스가 설정된다.

타이머 시작버튼(Reset) 입력이 감지되면 ioctl : COMMAND 명령어를 통해 타이머가 시작된다. 설정된타이머가종료되면 3초후에프로그램도종료된다.


Embedded System Software 2 / 4


Embedded System Software 3 / 4


Embedded System Software 4 / 4


제출방법

아래제출파일을사이버캠퍼스에 업로드

[프로그램제출란]

소스코드, Makefile, Readme 파일을 모두 포함한 [HW2]학번.tar.gz Ex) [HW2]20240000.tar.gz

소스코드구분

app 폴더 (소스코드, Makefile)

module 폴더 (소스코드, Makefile)

파일압축방법 : 학번폴더를생성하고, 그안에숙제관련 폴더(파일)을저장한뒤, 학번폴더가있는 위치에서 tar –cvzf [HW2]학번.tar.gz ./학번폴더

[보고서제출란]

[HW2]학번_reprt.pdf

Ex) [HW2]20240000_report.pdf

제공되는보고서형식참고. 세부 목차/내용추가가능.

본인의 응용 프로그램과 ioctl 동작을 설명하는 Flowchart 가 반드시 포함되어야 함.

보고서는반드시 PDF로제출

Due Date : 프로그램 – 2024 년 5 월 17 일 금요일 23:59

보고서 – 2024 년 5 월 19 일일요일 23:59

평가내용

프로그램 100점(주석점수포함), 보고서 20점.

Late : 하루에 10% 감점

Due Date 기준 프로그램은 +5 일까지, 보고서는 +3 일까지.

제출형식틀린경우 5% 감점.

Copy 적발 시 0 점.

Copy 의심자는 조교와 면담을 통해 소명해야 함.

참고자료

제공된 driver 압축 파일은 fpga device driver module 소스코드가 포함되어 있는 fpga 제어 방법에 대한 참고자료입니다.

채점 시 해당 device driver 모듈들을 insmod 하지 않습니다. 과제 프로그램 작성에 참고하시기 바랍니다.
