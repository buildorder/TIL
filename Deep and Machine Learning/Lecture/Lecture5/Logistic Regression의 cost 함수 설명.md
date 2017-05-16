## Logistic Regression의 cost 함수 설명

### Linear Regression에서의 Cost function의 문제점
\[ cost = \frac{1}{m} \sum_{m}^{i=1}(H(x^i) - y^i)^2 \]

\[H(x) = \frac{1}{1+{e}^{-W^TX}}\]

위와 같은 Cost function에서 **Linear regression** 은 일정하게 내려가는 모양을 가지지만 **Logistic Regression의 Hypothesis에 대한 Cost 함수는** 구불한 모양을 가지기 때문에 **Gradient descent** 함수에서는 시작점에 따라  **Local minimum** 에 도달 할 수 있다. 목표는 **Global Minimum** 이다

### Cost function
\[cost(W) = \frac{1}{m}\sum c(H(x), y)\]

Cost 함수는 하나의 Element의 코스트 값을 구하고 전부 더해서 평균 값을 냅니다

\[c(H(x), y)=\begin{cases}
 & \text{ -log(H(x))  : y =1}  \\
 & \text{ -log(1 - H(x)) : y=0 }   
\end{cases}\]

Cost 함수는 y가 1인경우와 0인경우로 나뉘게 됩니다.

![y=1](-log(x).png)

위 그래프는 y가 1일 때의 그래프 입니다. 그래프를 보는 대로 H(x)가 0에 가까워 질수록 **무한대에 가까워지고** 1에 가까워 질수록 **0에 가까워 집니다**

![y=0](-log(1-x).png)

위 그래프는 y가 0일 때의 그래프 입니다. 그래프를 보는 대로 H(x)가 0에 가까워 질수록 **0에 가까워 지고** 1에 가까워 질수록 **무한대에 가까워 집니다**

\[c(H(x), y) = -ylog(H(x)) - (1-y)log(1 - H(x))\]
위에서 나온 식들의 IF condition을 없애고자 하여 두 식을 합치면 바로 위에 나온 식과 같이 됩니다. **y에 따라 식의 모양이 바뀌게 됩니다**

\[c(W) = \frac{1}{m}\sum -ylog(H(x)) - (1-y)log(1 - H(x))\]
결론적으로 현재 코스트는 위와 같은 식으로 구할 수 있습니다

#### Reference
이 문서는 하단 주소의 내용을 기반으로 작성하였음을 알립니다

http://hunkim.github.io/ml/
