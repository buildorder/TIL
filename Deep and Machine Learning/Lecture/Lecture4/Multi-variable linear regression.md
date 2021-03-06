### Multi-variable linear regression

#### 여러개의 INPUT 데이터
| $X_1$ | $X_2$ |$X_3$ |  Y  |
|:--:|:--:|:--:|:---:|
| 73 | 80 | 75 | 152 |
| 93 | 88 | 93 | 185 |
| 89 | 91 | 90 | 180 |

>하나의 열이 하나의 **Instance**

위와 같이 데이터가 여러개인 경우에는 이전과 같은 방식의 **Hypothesis로 학습을 할 수 없다**

$ H(x) = Wx + b$
이전에 INPUT이 하나였을 때 **Hypothesis** 가 위와 같은 모양 이였다면

\[  H(x_1, x_2, x_3) = w_1x_1+ w_2x_2+w_3x_3 + b \]

INPUT이 3개라면 **Hypothesis** 는 이런 모양이 될 것이다

#### Matrix

위에서 설명한대로 INPUT이 많아질 때마다 **Hypothesis**를 수정한다면 귀찮은 작업이 된다

행렬곱을 생각해보자 (오직 곱만)

\[\begin{pmatrix} x_1 &  x_2 & x_3 \end{pmatrix}
\begin{pmatrix}w_1\\ w_2 \\ w_3 \end{pmatrix}\
=  (w_1x_1+ w_2x_2+w_3x_3)\]

위와 같이 행렬의 곱으로 나타낼 수 있습니다
이렇게 행렬로 나타낸다면 **Hypothesis**를 바꿀 필요가 없어지는 장점이 있다

이렇게 되면 **Hypothesis**는  
\[ H(X) = XW \]
* 관례적으로 X를 앞에다 쓴다

#### 다양한 Instance에서 Matrix 곱

\[\begin{pmatrix}
 {x}_{11}&{x}_{12}&{x}_{13} \\
 {x}_{21}&{x}_{22}&{x}_{23} \\
 {x}_{31}&{x}_{32}&{x}_{33} \\
 {x}_{41}&{x}_{42}&{x}_{43} \\
 {x}_{51}&{x}_{52}&{x}_{53} \\
\end{pmatrix} \bullet
\begin{pmatrix}
{w}_{1} \\
{w}_{2} \\
{w}_{3}
\end{pmatrix}
=
\begin{pmatrix}
 {x}_{11}{w}_{1}+{x}_{12}{w}_{2} +{x}_{13}{w}_{3}  \\
 {x}_{21}{w}_{1}+{x}_{22}{w}_{2} +{x}_{23}{w}_{3}  \\
 {x}_{31}{w}_{1}+{x}_{32}{w}_{2} +{x}_{33}{w}_{3}  \\
 {x}_{41}{w}_{1}+{x}_{42}{w}_{2} +{x}_{43}{w}_{3}  \\
 {x}_{51}{w}_{1}+{x}_{52}{w}_{2} +{x}_{53}{w}_{3}  \\
\end{pmatrix}
\]

위와 같은 Instance가 많은 데이터 들도 행렬 곱으로 한번에 원하는 결과를 얻을 수 있다
\[H(X) = XW\]
이런 **Hypothesis**로 정리 할 수 있다

위 행렬들의 Shape을 보면

X : [5, 3]  W : [3, 1]  H(X) : [5, 1]
세 가지로 이루어진 것을 볼 수 있다

* X행렬의 3부분이 W행렬의 3
* H(X)행렬의 1부분이 W행렬의 1이 된다
* 5부분은 행렬의 Instance의 갯수가 된다

이를 이용하여 데이터와 원하는 결과가 있을 때 W행렬을 설계할 수 있다
