# [백준] 5585번: 거스름돈

# 거스름돈

| 시간 제한 | 메모리 제한 | 제출 | 정답 | 맞힌 사람 | 정답 비율 |
| --- | --- | --- | --- | --- | --- |
| 1 초 | 128 MB | 39263 | 25469 | 21741 | 64.837% |

## 문제

타로는 자주 JOI잡화점에서 물건을 산다. JOI잡화점에는 잔돈으로 500엔, 100엔, 50엔, 10엔, 5엔, 1엔이 충분히 있고, 언제나 거스름돈 개수가 가장 적게 잔돈을 준다. 타로가 JOI잡화점에서 물건을 사고 카운터에서 1000엔 지폐를 한장 냈을 때, 받을 잔돈에 포함된 잔돈의 개수를 구하는 프로그램을 작성하시오.

## 입력

입력은 한줄로 이루어져있고, 타로가 지불할 돈(1 이상 1000미만의 정수) 1개가 쓰여져있다.

## 출력

제출할 출력 파일은 1행으로만 되어 있다. 잔돈에 포함된 매수를 출력하시오.

## 예제 입력 1

```
380
```

## 예제 출력 1

```
4
```

## 예제 입력 2

```
1
```

## 예제 출력 2

```
15
```

## 코드

```python
# Answer 1
num = 1000 - int(input())
count = 0

changes = [500, 100, 50, 10, 5, 1]

for change in changes:
    if num == 0: break
    else:
        count += num // change
        num %= change

print(count)

# Answer 2
num = 1000 - int(input())
count = 0
def change(money):
    global count, num
    k = num // money
    num -= money * k
    count += k
    
while num > 0:
    if num >= 500:
        change(500)
    elif num >= 100:
        change(100)
    elif num >= 50:
        change(50)
    elif num >= 10:
        change(10)
    elif num >= 5:
        change(5)
    else:
        count += num
        num = 0

print(count)
```
