# GPIO
**STM32F4xx family를 기준으로 한다**


### GPIO introduction
각각의 GPIO 포트는 아래의 종류별로 분리되는 레지스터들을 가지고 있다.

4개의 32bit Configuration 레지스터
* GPIOx_MODER
* GPIOx_OTYPER
* GPIOx_OSPEEDR
* GPIOx_PUPDR

두개의 Data 레지스터
* GPIOx_IDR
* GPIOx_ODR

한개의 Set/Reset 레지스터
* GPIOx_BSRR

한개의 Bit locking 레지스터
* GPIOx_LCKR

두개의 Alternate function selection 레지스터
* GPIOx_AFRH
* GPIOx_AFRL

### GPIO main features
* 16개 까지 통제가능
* 출력 상태 : push-pull 혹은 open drain + pull-up/down
* 출력 데이터는 output data register(GPIOx_ODR) 혹은 peripheral(alternate function output)
* 각각의 I/O마다 속도 선택
* 입력 상태 : floating, pull-up/down, analog
* 입력 데이터는 input data register(GPIOx_IDR) 혹은 peripheral(alternate function output)
* Bit set/reset register(GPIOx_BSRR)은 GPIOx_ODR에 비트 단위로 쓰기 위해 있다
* Locking mechanism (GPIOx_LCKR)은 I/O Configuration을 얼리기(freeze)를 제공한다
* Analog 기능
* Alternate function input/output 선택 레지스터 (I/O마다 많아봐야 16개)
* 두 클럭 사이클 안에 토글이 가능하다
* 크게 신축성 있는 pin multiplexing은 I/O를 GPIO혹은 몇몇개의 peripheral function으로 사용이 가능하다.
