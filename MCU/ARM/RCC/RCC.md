#RCC

### Clocks
System clock으로 구동되게 사용될 수 있는 3가지의 다른 clock source가 있다
* HSI oscillator clock
* HSE oscillator clock
* Main PLL (PLL) clock

장치들은 다음의 부가적인 clock source를 가지고 있다
* 32kHz low-speed internal RC (LSI RC), 독립된 watchdog, 그리고 선택적으로 Stop/Stanby 모드에서 Auto-wakeup을 위해 RTC를 구동하는데 쓰인다.
* 32.768kHz low-speed external crystal (LSE crystal), 선택적으로 RTC clock으로 구동한다.

각각의 clock source들은 power 소비량 optimize를 위해 독립적으로 switch되거나 off될수 있다.

몇몇개의 prescaler들이 **AHB frequency**, **high-speed** APB (APB2), **low-speed** APB (APB1) 들의 frequency범위를 설정하는데 사용된다.
* AHB의 최대 frequency는 180MHz이다.
* high-speed APB2의 허용되는 최대 frequency는 90MHz이다.
* low-speed APB1의 허용되는 최대 frequency는 45MHz이다.
