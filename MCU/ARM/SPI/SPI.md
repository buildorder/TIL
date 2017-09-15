# SPI

### SPI introduction

SPI interface는 두가지 주 기능을 제공한다, SPI protocol 혹은 I2S audio protocol 둘중 하나. 기본적으로, SPI function이 선택된다. software에 의해 SPI에서 I2S로 바꾸는 것이 가능하다.

SPI는 외부 장치와 half/full-duplex, 동기식 통신이 가능하다. interface는 master로 설정이 가능하며 이 경우에는 외부 slave device들에게 SCK을 제공한다. interface는 또한 multimatser 설정으로도 구동할 수 있다.

### SPI features
* 3가지 선으로 Full-duplex 동기식 통신
*
* 8bit 혹은 16bit 전송 frame format 선택
* Master 혹은 Slave 로 동작
* Multimaster 모드 기능
* Master 모드 buad rate prescalers
* Slave 모드 frequency
* master와 slave 간의 빠른 통신
*
* Programmable한 clock 극성과 phase
* Programmable한 data order(MSB-first 혹은 LSB-first)
* 
* SPI bus busy 상태 flag
* SPT TI 모드
* 신뢰할수 있는 통신을 위한 Hardware CRC 기능: Tx 모드에서 CRC value가 마지막 byte에 전송되어 질 수 있다. last byte가 도착했을 때 자동 CRC 에러 확인
* Master mode fault, overrun, CRC error들의 에러 flag와 interrupt 기능
*
