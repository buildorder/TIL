# OIL

## OIL 객체, 표준 속성 및 참조

### CPU
CPU는 다른 모든 객체의 container으로 사용된다.

### OS
OS는 OSEK application에 대한 OSEK OS의 특성을 정의하는데 사용된다.

CPU안에서 오직 하나의 OS만 정의 되어야 한다.

###### STATUS
STATUS 속성은 standard 혹은 extended 상태의 system을 사용해야 하는지 결정한다. 이 속성은 자동 할당되지 않는다.

이 속성은 ENUM type이고 다음 값중 하나이다.
* STANDARD
* EXTENDED

###### Hook routines
다음 속성 이름들은 OSEK OS에서 지원하는 hook routines에 대해 정의한다.
* STARTUPHOOK
* ERRORHOOK
* SHUTDOWNHOOK
* PRETASKHOOK
* POSTTASKHOOK

이 속성들은 BOOLEAN 타입이다.

만약 hook routine 이 사용된다면, value는 TRUE로 set되고 그렇지 않으면 FALSE로 set된다.

Error hook의 서비스 ID 및 context-related 정보에 대한 액세스 매크로의 사용은 BOOLEAN 유형의 다음 속성에 의해 활성화됩니다
* USEGETSERVICEID
* USEPARAMETERACCESS

###### USERSSCHEDULER
USERSSCHEDULER 속성은 BOOLEAN type이고 RES_SCHEDULER가 application에서 사용되는지 여부를 정의한다.

### TASK
TASK 객체는 OSEK의 task들을 대표한다.

###### PRIORITY
task의 priority는 PRIORITY 속성에 의해 결정된다.

이 값은 상대적인 값으로 이해해야 한다. 즉, PRIORITY의 값은 task의 상대적인 순서를 나타낸다. 이 속성의 type은 UINT32이다. OSEK OS는 가장 낮은 priority를 zero(0)로 정의한다. 더 큰 PRIORITY값은 더 높은 priority에 해당합니다.


###### SCHEDULE
SCHEDULE 속성은 task의 선점 가능권을 결정한다.

이 속성의 type은 ENUM이고 다음 중 하나의 값을 갖는다.
* NON
* FULL

이 속성의 FULL 값은 선점 가능(preemptable) task에 해당하고, 비선점(non-preemptable) task는 NON 값에 해당한다.

만약 SCHEDULE 속성이 NON으로 set되어 있다면, 이 task에 내부 자원이 할당 되지 않을 수도 있다.


###### ACTIVATION
ACTIVATION 속성은 task에 대한 대기중인 활성화 요청의 최대 수를 결정한다. 값이 1인경우 항상 하나의 활성화만 이 task대해 허용되었음을 나타낸다. 이 속성의 type은 UINT32이다.


###### AUTOSTART
AUTOSTART 속성은 task가 system start-up 절차에서 활성화 될지, 특정한 application mode에서 활성화 될지 결정한다. 이 속성의 type은 BOOLEAN이다. system start-up에서 task가 활성화 되어야 한다면, 값을 TRUE로 set한다. 그 외에는 값을 FALSE로 set한다.


### ALARM
ALARM은 특정 task를 활성화 하거나 비동기 알람을 사용될 수 있다. application mode에 따라 system start-up에서 자동적으로 alarm을 시작하는 것이 가능하다.

###### COUNTER
COUNTER 속성은 alarm에 할당된 counter을 나타낸다. 오직 한개의 counter가 alarm에 할당된다. 모든 alarm은 특정 counter에 할당되어야 한다.

###### ACTION
ACTION 속성은 alarm이 만료되었을 때. 사용될 알림의 유형을 정의한다. 이 속성은 다음과 같이 parameter가 있는 ENUM 이다.
* ACTIVATETASK {TASK_TYPE TASK;}
* SETEVENT {TASK_TYPE; EVENT_TYPE EVENT;}
* ALARMCALLBACK {STRING ALARMCALLBACKNAME;}

###### ACTION = ACTIVATETASK
task 속성의 PARAMETER은 alarm이 만료될 때 활성화 될 task를 정의한다.


### ISR
ISR 객체는 OSEK의 interrupt service routines을 대표한다.

###### CATEGORY
CATEGORY 속성은 ISR의 category를 정의한다. 이 속성은 UIN32 type이고 1 또는 2만 허용된다.

###### RESOURCE
RESOURCE 속성은 ISR에 의해 접근 가능한 자원들의 목록들을 정의한다. 이 속성은 RESOURCE_TYPE의 multiple 참조이다.

###### MESSAGE
MESSAGE 속성은 ISR에 의해 접근 가능한 메세지들의 목록을 정의한다. 이 속성은 MESSAGE_TYPE의 multiple 참조이다.
