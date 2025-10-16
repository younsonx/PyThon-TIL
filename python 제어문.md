# if문

조건의 참 거짓을 판명
```
money = 2000
if money >= 3000:
    print('택시를 타라')
else:
    print('걸어가라')

걸어가라
```

조건을 판단하기 위해 사용하는 다른 연산자로 and, or, not이 있다.
## and, or , not
```
money = 2000
card = True
if money >= 3000 or card:
    print('택시를 타라')
else:
    print('걸어가라')

택시를 타라
```

## in, not in
```
pocket = ['paper', 'cellphonre', 'money']
if 'money' in pocket:
    print("take a taxi")
else:
    print("walk away")

take a taxi
```

### pass
조건문에서 아무 일도 하지 않게 설정하고 싶을 떄 pass를 사용한다

주머니에 돈이 있으면 가만히 있고, 돈이 없으면 카드를 꺼내라는 예제
```
pocket = ['paper', 'cellphonre', 'money','card']
if 'money' in pocket:
    pass
else:
    print("walk away")
```

## 다양한 조건을 판단하는 elif

ex) 주머니에 돈이 있으면 택시를 타고, 주머니에 돈은 없지만 카드가 있으면 택시를 타고가고,
돈도 없고 카드도 없으면 걸어가라
```
pocket = ['paper', 'cellphone'] ## 주머니 안에 종이, 핸드폰이 있다
card = True ## 카드를 가지고있다
if 'money' in pocket:
    print('take a taxi')
else:
    if card:
        print('take a taxi')
    else:
        print('walk away')
```
이런 복잡함을 해결하기 위해 elif를 사용
```
pocket = ['paper', 'cellphone'] ## 주머니 안에 종이, 핸드폰이 있다
card = True ## 카드를 가지고있다
if 'money' in pocket: ##주머니에 돈이 있으
    print('take a taxi')
elif card: ## 주머니에 돈이 없고 카드가 있으
    print('take a taxi')
else: ## 주머니에 돈이 없고, 카드도 없으
    print('walk away')
```
elif는 이전 조건문이 거짓일때 사용됨. 또한 개수에 제한 없이 사용가능하다

## 조건부 표현식
코드를 간단히 표현 가능 
```
score = 60
if score >= 60:
    message = 'success'
else:
    message = 'failure'

print(message)
```
```
score = 60
message = "success" if score >= 60 else "failure"

print(message)
```
조건부 표현식은 
```
변수 = 조건문이 참인 경우의 값 if 조건문 else 조건문이 거짓인 경우의 값
```

# while 문
```
treeHit = 0
while treeHit < 10:
    treeHit += 1
    print('나무를 %d번 찍었습니다' % treeHit)
    if treeHit == 10:
        print('나무가 넘어갑니다')
```
문장을 반복해서 사용해야하는 경우 사용
```
prompt = """ 
1. add
2. del
3. list
4. quit

enter number : """ ## 문자열로 프롬포트 생

number = 0
while number != 4:
    print(prompt)
    number = int(input())
```
```
enter number : 
1

1. add
2. del
3. list
4. quit

enter number : 
2

1. add
2. del
3. list
4. quit

enter number : 
3

1. add
2. del
3. list
4. quit

enter number : 
4
```
## break 
=> while문 강제로 빠져나가기
```
coffee = 10
money = 300
while money:
    print('돈을 받았으니 커피를 준다')
    coffee -= 1
    print("남은 커피의 양은 %d개 입니다" % coffee)
    if coffee == 0:
        print('재고소진')
        break
```
```
돈을 받았으니 커피를 준다
남은 커피의 양은 9개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 8개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 7개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 6개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 5개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 4개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 3개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 2개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 1개 입니다
돈을 받았으니 커피를 준다
남은 커피의 양은 0개 입니다
재고소진
```
while 문을 이용해서 실제 커피머신 구현
```
coffee = 10
while True:
    money = int(input("돈을 널어주세요"))
    if money == 300:
        print("커피를 줍니다")
        coffee -= 1
    elif money > 300:
        print("거스름돈 %d원을 주고 커피를 줍니다" % (money - 300))
        coffee -= 1
    else:
        print("돈은 다시 돌려주고 커피를 주지 않습니다")
        print("남은 커피의 양은 %d개 입니다" % coffee)
    if coffee == 0:
        print('재고소진')
        break
```
## continue
while문의 맨 처음으로 돌아가기

1부터 10까지 숫자중 홀수만 출력하기
```
a = 0
while a < 10:
    a += 1
    if (a % 2) == 0 : continue
    print(a)

    
1
3
5
7
9
```
## 무한루프
무한루프는 while 문으로 구현할 수 있다.

```
while True:
  ~~~~~~~~~~
```
while문의 조건이 항상 참이므로 항상 참이 된다 따라서 while문 안의 문장들은 무한히 수행될 것 이다.

# for 문
for문 의 기본구조
```
for 변수 in 리스트(또는 튜플, 문자열):
  ~~~~~~
```
영어로 직관적인 해석을 해보았을때 리스트의 값으로부터 변수에 대입한다는 느낌

ex) for i in test_list

test_list 로 부터 i에 대입
```
marks = [90, 25, 67, 45, 80]
num = 0 #학생들에게 붙여줄 번호

for score in marks:
    num += 1 
    if score >= 60:
        print("number of %d student is pass"%num)
    else:
        print("number of %d student is fail"%num)
```

## for문에서 continue응용
```
marks = [90, 25, 67, 45, 80]
num = 0

for score in marks:
    num += 1
    if score < 60:
        continue
    else:
        print('congratulation! student %d is pass' %num)
```

## for문에서 자주사용하는 range함수

range() => 숫자 리스트를 자동으로 만들어주는 함수
```
a = range(10)
a
0,1,2,3,4,5,6,7,8,9
```
마지막 숫자는 포함하지 않는다. 또한

range(시작번호, 끝번호) 형태로도 사용가능

range 함수를 이용하여 아까전의 예제를 좀 더 간결하게 만들 수 있다
```
marks = [90, 25, 67, 45, 80]
for num in range(len(marks)): #번호 생성 
    if marks[num] < 60: #인덱스 활용 
        continue
    else:
        print('congratulation! student %d is pass' %num)
```

## 리스트 컴프리헨션
리스트 안에 for문을 포함하는 표현식

표현식
```
[표현식 for 항목 in 반복가능객체 if조건문]
```
if조건문 부분은 생략 가능 
```
a = [1, 2, 3, 4]
result = []
for num in a:
    result.append(num*3)

print(result)
```
리스트 컴프리헨션 사용
```
a = [1, 2, 3, 4]
result = [num*3 for num in a]
print(result)
```
if조건문 추가
```
a = [1, 2, 3, 4]
result = [num*3 for num in a if num%2 != 0]
print(result)
```





