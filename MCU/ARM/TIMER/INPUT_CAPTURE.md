# INPUT Capture

### INPUT Capture
Input capture mode에서, **Capture/Compare** Register는 해당하는 ICx 신호에 의해 감지된 전이 후에 counter의 값을 latch하기 위해 사용된다. Capture이 일어날 때, 해당하는 **CCxIF** flag가 set되고 그리고 만약 interrupt나 DMA가 enable됬다면 request가 보내진다. 만약 **CCxIF** flag가 이미 HIGHT일 때 capture가 일어난다면, over-capture flag **CCxOF** 가 set된다. **CCxIF** 는 software에 의해 0을 씀으로서 혹은 **TIMx_CCRx** regitser에 저장된 captured data를 읽음으로서 clear된다. **CCxOF** 는 0으로 쓰여질때 clear된다.

TI1의 input이 rise가 됬을 때 **TIMx_CCR1** 의 counter value를 capture하는 방법이다 :
* 활성화된 input을 선택한다: **TIMx_CCR1** 은 **TI1** input과 반드시 연결되어야 한다, 그러므로  **TIMx_CCMR1** regitser의 **CC1S** bit에 01을 써주자. **CC1S** 가 00이 아니게 되자마자, channel은 input으로 설정되고 TIMx_CCR1 regitser는 read-only가 된다
* Timer에 연결된 신호에 대하여 input filter duration을 program 해야한다. 상상해보자, toggling 할 때, input 신호는 많으면 5개의 internal clock cycles 동안 안정적이지 않다.
* 
