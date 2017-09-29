# bxCAN

### bxCAN introduction
**bxCAN** 이라 불리우는 **Basic Extended CAN** peripheral은 CAN network를 interface합니다. 이것은 CAN protocol version 2.0A와 2.0B를 지원합니다. 최소 CPU load로 많은 수의 수신 메세제를 효율적으로 관리할수 있도록 설게되었습니다. 또한 전송 메세지의 우선순위 요구사항을 충족시킵니다.

 safety-critical 어플리케이션인 경우에는, CAN 컨트롤러는 **CAN Time Triggered Communication** 옵션을 지원하기 위해 모든 hardware function을 제공해야 한다.

#### bxCAN main features
* CAN protocol 2.0A, 2.0B를 지원
* 1 Mbit/s 통신속도
* SOF 전송에서 Time Stamp

#### Reception
* 3 단계가 있는 2개의 수신 FIFO
* Scalable한 filter bank : CAN1과 CAN2간에 공유되는 28개의 filter bank
* 식별자 목록 기능
* 설정가능한 FIFO overrun
* SOF 수신시 Time Stamp

#### Timer-triggered communication option
* 자동 재전송 모드 비활성화
* 16-bit free running timer
* 마지막 두 byte에 Time Stamp 전송

#### Management
* Maskable interrupts
* 독자적인 address space에 Software-efficient mailbox에 매핑

#### Dual CAN
* CAN1 : Slave bxCAN과 512-byte SRAM memory간에 통신 managing을 위한 Master bxCAN
* CAN2 : Slave bxCAN, SRAM memory와 direct access memory 불가
* 두개의 bxCAN cell들은 512-byte SRAM memory를 공유한다

### bxCAN general description
요즘의 CAN application들은, network에서 node들의 숫자가 증가하고 종종 몇개의 network들이 gateway를 통해서 같이 연결되어진다. 일반적으로 시스템에서 메세지의 숫자는 상당히 증가했다. 게다가 application message외에도 Network Management 그리고 Diagnostic message가 도입되었습니다.

* 각 타입의 message를 다루기 위해 강화된(enhanced) filetering mechanism이 요구된다.

게다가, application task들이 CPU 시간을 더 필요로 하므로 message 수신으로 인해 발생되는 real-time 제약이 감소되어야 한다.

* 수신 FIFO 방식은 CPU가 application task를 message 손실 없이 오랜 기간동안 수행할 수 있도록 해준다.

CAN driver기반의 표준 HLP는 CAN controller에 효율적인 interface를 필요로 합니다.

#### CAN 2.0B active controller
bxCAN module은 전부 자체적으로 CAN message의 송신 및 수신을 다룬다. Standard 식별자(indentifiers) (11-bit) 그리고 extended 별자(indentifiers) (29-bit)들은 전적으로 하드웨어에 의해 지원된다.

#### Control, status and configuration registers
application은 이 레지스터들을 이렇게 사용한다 :
* CAN parameter 설정, e.g. buad rate
* 전송 요청
* 수신 handle
* interrupt 관리
* 진단 정보 get

#### Tx mailboxes
3개의 전송 mailboxes들이 message를 set up하기 위해 software에 제공되어 진다. 전송 스케쥴러가 어느 mailbox가 첫번째로 전송될지 결정한다.

#### Acceptance filters
bxCAN은 software가 필요로 하는 message를 선택하고 다른 것들은 버리기 위해 28개의 설정가능한 식별자(identifier) bank를 제공한다.

#### Receive FIFO
두개의 receive FIFO들이 수신 message들을 저장하기 위해 하드웨어에 의해 사용된다. 3개의 완료 message들은 각각의 FIFO에 저장될 수 있다. FIFO들은 전적으로 하드웨어에 의해 관리된다.

### bxCAN operating modes
bxCAN은 3가지 작동 모드를 가지고 있다 : initialization, normal 그리고 Sleep. hardware reset후에 bxCAN은 파워 소비를 줄이기 위해 Sleep 모드가 되고, CANTX에는 내부 풀업이 활성화 된다. CAN_MCR register의 INQR이나 SLEEP bit를 setting 함으로써 initialization 이나 Sleep 모드에 들어갈 수 있다. 모드에 들어갔을 때, bxCAN은 CAN_MSR reigster의 INAK 혹은 SLAK bit를 set 함으로써 확실하게 하고, 내부 풀업을 비활성화 한다. INAK 혹은 SLAK 둘다 set되지 않았으면, bxCAN은 normal mode이다. normal mode에 들어가기 전에 bxCAN은 항상 CAN bus에 동기화 되어야 한다. 동기화 하기 위해서, bxCAN은 CAN 버스가 idel 상태가 되기까지 기다립니다, 이는 CANRX에서 11개의 연속적인 recessive bit가 모니터링 되었음을 뜻합니다. 
