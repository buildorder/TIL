# ADC

### ADC introduction
12-bit의 ADC는 연속적으로 근사치를 구하는 analog-to-digital converter이다. 이것은 16개의 외부 source, 2개의 내부 source, 그리고 Vbat channel로부터 신호 측정을 가능하게 하는 19개의 multiplexed channel이 있다. channel들의 A/D 변환은 single, continuous, scan 혹은 discontinuous mode로 수행될 수 있다. ADC의 결과는 left-aligned 혹은 right-aligned된 16bit data regitser에 저장된다.

### ADC main features
* 12-bit, 10-bit, 8-bit, 6-bit의 설정 가능한 분해능
* end of conversion, end of injected conversion, analog watchdog, overrun event 들이 일어날때 interrupt 발생
* Single 그리고 continuous 변환 모드
* channel 0부터 channel 'n'까지 자동 conversion을 위한 scan mode
* Data alignment와 내장된 data 일관성 (?)
* Channel별로 programmable한 sampling time
* regular와 injected 변환 둘개를 위한 External trigger의 configurable한 polarity 옵션
* Discontinuous mode
* Dual/Triple mode (장치에 ADC가 2개 혹은 그 이상 있을 때)
* Dual/Triple mode에서 설정가능한 DMA data storage
* ADC 변환 type
* ADC 공급에 필요한것 : 2.4V에서 3.6V까지 full speed 그리고 1.8V에서 slower speed
* ADC 입력 범위 : Vref- <= Vin <= Vref+
* 일반 channel conversion에 DMA request generation

### ADC clock

ADC는 두가지 클럭을 방식을 특징으로 가진다 :
*
