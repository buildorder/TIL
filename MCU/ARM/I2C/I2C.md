# I2C

### I2C introduction
I2C bus interface는 microcontroller와 serial I2C bus 사이에서 interface로서 제공한다. 이것은 multimaster 기능, 그리고 I2C bus-specific sequencing, protocol, 중재 그리고 timing을 control한다. 이것은 standard mode(Sm, 100kHz까지) 그리고 Fm mode(Fm, 400kHz까지)를 지원한다.

이것은 CRC 생성 및 확인, SMBus(system management bus) 그리고 PMBus (power management bus)를 포함한 다양한 목적들에 사용된다.

### I2C main features
* 병렬 버스/I2C protocol conveter
* Multimaster 기능: 똑같은 interface가 Master혹은 Slave로 동작 가능
* I2C Master 기능: 클럭 생성, Start와 Stop 생성
* I2C Slave 기능: Programmable한 I2C 주소 감지, 2개의 slave address로 Dual adderessing 기능, Stop bit 감지
* 7-bit/10-bit adderssing 그리고 General Call 생성 혹은 감지
* 다른 통신 속도 지원: Standard speed(100kHz), Fast speed(400kHz)
* Analog 노이즈 필터
* 상태 flags : Transmitter/Receiver mode flag, End-of-Byte 전달 flag, I2C busy flag
* 에러 flags : master mode에서 중재기 lost 상태, address/data 전달 후에 acknowledgment 실패, 잘못 배치된 start 혹은 stop 상태 감지, 만약 clock stretching이 disable이라면 Overrun/Underrun
* 두개의 interrupt vector: address/data 통신 성공, 에러 컨디션
* 선택할수 있는 clock stretching
* DMA 기능과 1-byte buffer
*
