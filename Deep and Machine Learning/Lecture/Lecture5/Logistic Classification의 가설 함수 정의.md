## Logistic Classification의 가설 함수 정의

###  Binary Classification

0이나 1으로 Encoding 하는 경우가 많다. 예를 들어
* 스팸과 햄
* 타임라인 Show 아니면 Hide
* 주식 팔까 살까

### Linear regression의 문제

1. 모든 데이터들의 기준으로 Cost가 가장 작은 Hypothesis를 찾기 때문에 Classification에서 잘못 될 수 있다

2. Hypothesis가 0보다 작거나 1보다 훨신 클 수 있다

### Logistic Hypothesis

\[H(x) = Wx + b\]

기존의 Hypothesis를 0 ~ 1 사이로 좁힐 필요가 있다

#### Sigmoid 함수
위에서 H(x) 함수를 z라고 두자
\[g(z) = \frac{1}{1+{e}^{-z}}\]

![sigmod](./sigmoid.gif)

* z가 커질수록 1에 가까워 지고
* z가 작아질수록 0에 가까워 진다

#### Reference
이 문서는 하단 주소의 내용을 기반으로 작성하였음을 알립니다

http://hunkim.github.io/ml/

http://tikalon.com/blog/blog.php?article=2011/sigmoid
