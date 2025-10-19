# 사용자 입력 활용하기

## input 사용하기
```
a = input()
life is too short
a
'life is too short'
```
input은 사용자가 키보드로 입력한 모든것을 문자열로 저장한다.

## 프롬포트를 띄워 사용자 입력 받기
```
number = input("숫자를 입력하세요: ")
숫자를 입력하세요: 3
print(number)
3
```
마찬기지로 input은 입력되는 모든것을 문자열로 저장하기 때문에 number은 숫자가 아닌 문자열로 취급된다.

# print문 자세히 알기
지금까지 사용한 print문은 데이터를 출력하는 용도이다.  
print문으로 할 수 있는 또 다른 예시로는 

## 큰따옴표로 둘러싸인 문자열은 + 연산과 동일하다
```
print("Life" "is" "too" "short")
Lifeistooshort
```

## 문자열 띄어쓰기는 쉼표로 한다
```
print("Life", "is", "too", "short")
Life is too short
```

## 한 줄에 결괏값 출력하기
```
for i in range(10):
    print(i, end=' ')

    
0 1 2 3 4 5 6 7 8 9
```
매개변수 end를 사용해 끝 문자를 지정해야한다.




