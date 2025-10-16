### Level 2

⚙️ 중간 난이도 (Level 2)

1.
3의 배수의 합 구하기  
1부터 100까지의 수 중 3의 배수의 합을 구하세요.

2. 
별 찍기 (삼각형)  
다음과 같은 형태로 별(*)을 출력하세요.
```
*
**
***
****
*****
```
3. 
while문으로 5의 배수 찾기  
1부터 50까지의 수 중 5의 배수만 출력하세요.

1. sol
```
num = 0

for i in range(1, 101):
    if i % 3 == 0:
        num += i
    else:
        continue

print(num)
```
```
1683
```

2. sol
```
for i in range(1, 6):
    print("*"*i)
```
```
*
**
***
****
*****
```

3. sol
```
num = 0

while num < 51:
    num += 1
    if num % 5 != 0:continue
    print(num)
```

### Level 3

🧠 심화 난이도 (Level 3)  

1. 리스트에서 양수만 출력하기  
다음 리스트 numbers = [3, -2, 0, 5, -7, 9]에서 양수만 출력하세요.

2. 구구단 2단 출력  
for문을 이용해 다음과 같이 2단을 출력하세요.  
```
2 x 1 = 2  
2 x 2 = 4  
...  
2 x 9 = 18  
```
3. break와 continue 사용하기  
1부터 20까지의 숫자를 출력하되,  
3의 배수는 건너뛰고(continue)  
15가 되면 반복을 멈추도록(break) 하는 코드를 작성하세요.

4. 사용자 입력 반복문  
사용자가 "exit"를 입력할 때까지 계속 문자열을 입력받아 출력하는 프로그램을 작성하세요.

1. sol
```
numbers = [3, -2, 0, 5, -7, 9]
for num in range(len(numbers)):
    if numbers[num] <= 0:continue
    print(numbers[num])
```
```
3
5
9
```
다른 풀이 ChatGPT
```
기본 접근

numbers = [3, -2, 0, 5, -7, 9]
for num in numbers: #num에 numbers를 그대로 대입
    if num > 0:
        print(num)
```
```
continue활용
numbers = [3, -2, 0, 5, -7, 9]
for num in numbers:
    if num <= 0:
        continue
    print(num)
```
```
리스트 컴프리헨션
numbers = [3, -2, 0, 5, -7, 9]
positives = [num for num in numbers if num > 0]
print(positives)
```
2. sol
```
for i in range(2,3):
    for j in range(1,10):
        print("%d x %d = %d" %(i, j, i*j))
```
```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
```
ChatGPT
```
f포매팅 활용
for i in range(2, 3):
    for j in range(1, 10):
        print(f"{i} x {j} = {i*j}") # f포매팅
```

3. sol
```
for i in range(1,21):
    i += 1
    if i == 15:break
    if i % 3 == 0:continue
    print(i)
```
chatGPT comment
```
🚫 문제점
i += 1 때문에 실제 출력이 한 칸 밀려버려.
즉, 2부터 시작하고 15 이전에 끝남.

for i in range(1, 21):
    if i == 15:
        break
    if i % 3 == 0:
        continue
    print(i)
```

4. sol
```
while True:
    strings = input("문자열을 입력하세요 : (종료 exit)")
    if strings == "exit":
        print("프로그램을 종료합니다")
        break
    print("입력한 내용: ", strings)
```






















