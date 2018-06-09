# array slice in python

slice는 `start:stop[:step]`의 형식으로 사용한다. (step은 옵션)

step을 명시하지 않을 경우에는

``` python3
a[start:end] # start부터 end-1까지의 item
a[start:] # start부터 리스트 끝까지 item
a[:end] # 처음부터 end-1까지의 item
a[:] # 리스트의 모든 item
```

step 을 명시하는 경우에는

`a[start:end:step]`# start부터 end-1까지 step만큼 인덱스 증가시키면서 item을 포함시킨다.

또 start나 end가 음수가 음수인 경우에는 리스트의 끝에서부터 아이템을 포함하겠다는 것이다.

``` python3
a[-1] # 맨 뒤의 item
a[-2:] # 맨 뒤에서부터 item2개
a[:-n] # 맨 뒤의 item n개 빼고 전부
```

``` python3
a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print "a =", a
print "a[0:1]:", a[0:1]
print "a[0:10]:", a[0:10]
print "a[0:20]:", a[0:20]
print "a[0:10:2]:", a[0:10:2]
print "a[:-1]:", a[:-2]
print "a[:-30]:", a[:-30]
```
```console
a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
a[0:1]: [0]
a[0:10]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
a[0:20]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
a[0:10:2]: [0, 2, 4, 6, 8]
a[:-1]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
a[:-30]: []
```

## 참고
[파이썬 3 document](https://docs.python.org/3.6/library/stdtypes.html#common-sequence-operations)
[파이썬 slice notation(: 쓰는거)좀 알려주세요](https://hashcode.co.kr/questions/74/%ED%8C%8C%EC%9D%B4%EC%8D%AC-slice-notation-%EC%93%B0%EB%8A%94%EA%B1%B0%EC%A2%80-%EC%95%8C%EB%A0%A4%EC%A3%BC%EC%84%B8%EC%9A%94)