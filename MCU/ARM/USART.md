# USART

### USART instroduction
* USART는
* USART는 fractional한 baud rate gernerator를 사용해서 매우 넓은 범위의 baud rate들을 지원합니다.

* 이것은 단방향 통신 그리고 single wire인 반이중 통신을 지원합니다.
* 이것은 또한 LIN, Smartcard Protocol 그리고 IrDA SIR ENDEC 규격, 그리고 modem operations를 지원합니다.

* 빠른 속도의 data communication도 multibuffer configuration을 위해 DMA를 사용함으로서 사용이 가능합니다.

### USART main features
* 전이중, 비동기식 통신
* NRZ 표준 포맷
*
* fractional한 baud rate generator 시스템
>
* Progrmmable한 data word 길이 (8에서 9 bits)
* 설정가능한 stop bits - 1 혹은 2 stop bit를 지원
*
* 전송 동기화를 위한 전송기 clock output
* IrDA SIR encoder decoder
>
*
>
>
* Single-wire 반이중 통신
* 설정가능한 DMA를 사용한 multibuffer communication
>
* 전송기와 수신기를 위해 enable bits를 분리(?)
* 전송 감지 flags:
  1. Receive buffer full
  2. Transmit buffer empty
  3. End of transmission flags
* Parity control:
  1. Transmits parity bit
  2. 받은 데이터 parity 체크
* 4개의 에러 감지 flags:
  1. Overrun 에러
  2. Noise 에러
  3. Frame 에러
  4. Parity 에러
* 열개의 interrupt sources 및 flags:
  1. CTS 변화
  2. LIN break 감지
  3. 전송 데이터 register 빔
  4. 전송 완료
  5. 수신 데이터 register 꽉참
  6. Idle line 수신
  7. Overrun 에러
  8. Framing 에러
  9. Noise 에러
  10. Parity 에러
* Multiprocessor communication - 만약 address 일치가 발생하지 않는다면 mute mode에 들어감
* mute mode로부터 일어남 ()
* 두개의 수신 wakeup modes: Address bit(MSB, 9th bit), Idle line

### USART function description
interface는 외부적으로 다른 장치와 3가지 핀으로 연결된다. 양방향의 통신이 필요한 모든 USART는 최소한의 두 핀이 필요하다 : RX와 TX.

RX : Receive Data Input은 serial data input이다. Oversampling 기술은 들어오는 유효한 데이터와 noise를 구분하므로서 data recovery에 사용된다.

TX : 전송 Data 출력. 전송기가 disable 됐을 때, 출력 핀은 I/O 포트 configuration으로 돌아간다. 전송기가 사용 가능하지만 아무것도 전송할게 없을때, TX핀은 high level이다. Single-wire 그리고 Smartcard 모드일때, 이 I/O는 data를 송수신한다 (USART level에서, SW_RX에서 data가 수신된다).


### Fractional baud rate generation
수신기와 송신기를 위한 baud rate는 USARTDIV에 프로그래밍된 Mantissa값과 Fraction 값이 같게 설정되어야 합니다.
