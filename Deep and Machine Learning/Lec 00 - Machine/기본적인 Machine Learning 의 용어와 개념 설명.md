### 기본적인 Machine Learning 의 용어와 개념 설명

#### Machine Learning
> **Explcit Programming** 의 한계

    스팸필터 : 많은 규칙
    자율주행 : 너무나 많은 규칙

> **Machine Learning** 이란

    프로그램이지만 개발자가 직접 정하지 않고 프로그램 자체가 자료나 현상에서 직접 학습해서 무언가를 배우는 능력을 갖는 프로그램

#### 학습 방법 - Supervised / Unsupervised Learning
> **Supervised Learning**

    label(training set)이 정해진 데이터를 가지고 학습하는 방식

>> **Supervised Learning** 의 작동 방식

    Lable된 데이터 -> Machine Learning 모델

레이블된 데이터로 Machine Learning 모델에 학습을 시킨다.

    데이터를 가지고 질문 -> Machine Learning 모델 -> 대답

Machine Learning 모델에 질문을 하면 학습된 데이터를 바탕으로 대답을 해준다.

위와 같이 Label된 데이터의 모음을 **Training Data Set** 이라 부른다.

>> **Supervised Learning** 의 종류

    1. Regression
        - 범위가 넓은 분류를 한다

    2. Binary Classification
        - 이진으로 분류를 한다

    3. Multi-label Classification
        - 등급으로 분류를 한다

> **Unsupervised Learning**

    label이 없는 데이터를 보고 스스로 학습하는 방식
