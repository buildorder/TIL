### Linear Regression의 Hypothesis 와 cost 설명

#### Linear Regression 이란

여러 데이터들이 퍼져있는 형태에서 일정한 패턴을 찾아내고, 그 패턴에서 무엇인가 예측하는 것

* 학습되어 생성된 모델에 입력을 넣으면 학습된 정보를 기반으로 출력을 해준다
* **Data가 Linear한 모델** 이여야 한다
* 세상에 있는 많은 현상들이 Linear한 경우가 많음

#### 가설 (hypothesis)
$ H(x) = Wx + b $
위와 같이 **Linear** 한 모델에서 Data에 맞는 W와 b를 구하는 것이 목적

#### Cost function ( Loss function )
Model을 만들 때 어느 Model이 더 좋은지 판단할 필요기 때문에
현재 만들어진 모델이 실제 데이터와 차이가 얼마나 큰지 확인 하는 함수

$ (H(x) - y)^2 $
위의 식과 같은 방식으로

$$ cost = 1/m \sum_{m}^{i=1}(H(x^i) - y^i)^2 $$
모델 전체에 적용시키게 된다면 위와 같은 식이 된다

#### Linear Regression의 목표
Cost 값이 가장 **작은** W와 b값을 구하는 것이 목표
