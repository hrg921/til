# list comprehension in python

comprehension은 '이해'라는 뜻을 가진다.

우리는 종종 for-loop을 이용하기 위해 배열을 만들기도 하지만 배열을 만들기 위해 for-loop을 이용하기도 한다.

C언어와 같은 저급언어에선 for-loop과 배열의 선언이 반드시 명확해야 했으나 python은 높은 추상화 수준을 발휘하여 이를 편하게 해준다.

특히 배열을 만들 때 (리스트를 만들 때), list comprehension이라는 문법을 이용하여 이를 간편히 처리할 수 있다.

예를 들어 1~10까지의 제곱근이 들어있는 배열을 만든다고 생각해 보자. 기존의 언어들은 다음과 같은 방식으로 구현해야 한다.

```python3
from math import sqrt

sqrts = []
for x in range(10):
	sqrts.append(sqrt(x + 1))
```

for-loop또한 때때로 불필요하게 보일때가 있다. 너무 긴 것 같은 기분이 들어 함수형 패러다임을 조금 적용하면 다음과 같이 작성할 수 있다.

```python3
from math import sqrt

sqrts = list(map(lambda x: sqrt(x+1), range(10)))
```

이를 list comprehension이라는 문법을 적용하면 다음과 같이 쓸 수 있다.

```python3
from math import sqrt

sqrts = [sqrt(x + 1) for x in range(10]
```

사용되는 함수들이 줄고 가독성도 높아졌다.

복잡한 list comprehension은 다음과 같이 순차적인 블록으로 이해하면 된다.

```python3
combs = [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
```

->

```python3
combs = []
for x in [1,2,3]:
    for y in [3,1,4]:
        if x != y:
            combs.append((x, y))
```

## 참고
[python official documents](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)