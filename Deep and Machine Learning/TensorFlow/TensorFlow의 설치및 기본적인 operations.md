## TensorFlow의 설치 및 기본적인 operations

### TensorFlow란
**Data Flow Graph** 를 사용해서 **Numerical Computation** 을 하는 라이브러리

> **Data Flow Graph** 란

    Node : 수학적인 연산을 뜻함
    Edge : 다양한 데이터 어레이들을 뜻함

**Node** 와 **Edge** 를 거치면서 내가 원하는 결과를 얻는 그래프
**Data** 가 흐르는 것을 **Tense** 라고 한다

### TensorFlow의 구동 방식

1. 텐서플로우의 연산자들을 사용하여 그래프를 만든다
2. 그래프를 실행시킨다
3. 값이 업데이트 되거나 리턴을 받는다

### 함수

#### Placeholder

    객체 = tf.placeholder(자료형)
그래프의 노드에 실행시키는 단계에서 값들을 넣고 싶을 때 사용

    feed_dict={argue1 : x, argue2 : x, ...}
이렇게 안에 값을 넣어준다

### Rank / Shape / Type

#### Rank
몇 차원 Array인지 알려준다

    0 :  스칼라
    1 :  1차원 배열
    2 :  2차원 배열
    ....

#### Shape
텐서의 모양

    t = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
이런 배열이 있을 때

Shape는 [3, 3]

#### Types

자료형
1. **tf.float32** : FLOAT
2. **tf.float64** : DOUBLE
...
