# 파일 생성하기
맥에서 파일을 생성하려면 내 맥북 기준으로 
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt", 'w', encoding='utf-8')
f.close()
```
여기서 encoding='utf-8'은 문자 인코딩 방식이 조금 다르기 때문에 출력할때 글자가 깨지지 않도록 설정해주는 것이다.

내 맥북 문서에 새파일을 생성하여 1번째 줄 부터 10번쨰 줄 까지 출력하는 파일을 만들어보면  
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt", 'w', encoding='utf-8')
for i in range(1,11):
    data = "%d번째 줄 입니다\n" %i
    f.write(data)
f.close()
```
라고 작성한 후 터미널에서 결과를 보면 
```
Last login: Sun Oct 19 19:25:50 on ttys015
gwag-yunseong@gwag-yunseong-ui-MacBookAir ~ % cd Documents
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3 write_data.py
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents %
```
라고 뜨고 이 실행결과를 보려면  
finder -> 문서 -> 새파일.twt를 클릭하면 실행 결과가 나와있다.  

기존의 print문과 다른 방식은  
print문을 활용하면 모니터 화면에 데이터를 출력하는 방식이지만,
이 방법은 모니터 화면 대신에 파일에 데이터를 적는 방법이다.

파일 열기 모드에는 다음과 같은 것들이 있다.
```
r => 읽기 모드: 파일을 읽기만 할 때 사용한다.
w => 쓰기 모드: 파일에 내용을 쓸 때 사용한다.
a => 추가 모드: 파일의 마지막에 새로운 내용을 추가할 때 사용한다.
```

# 파일을 읽는 여러가지 방법

## readline 함수 이용하기
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt", 'r')
line = f.readline()
print(line)
f.close()
```
이는 '새파일.txt' 파일을 읽기모드로 연 후 readline을 이용하여 파일의 첫 번쨰 줄을 출력한다
```
1번째 줄 입니다
```
모든 줄을 읽어 화면에 출력하기 위해선
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'r')
while True:
    line = f.readline()
    if not line: break
    print(line)
f.close()
```
무한루프 안에서 f.readline()을 사용해 파일을 계속 한 줄씩 읽어들인다.  
더이상 읽을 줄이 없으면 break를 수행한다.  
readline은 더 이상 읽을 줄이 없으면 문자열('')을 리턴한다.
(한 줄씩 읽어 출력할 때 줄 끝에 \n이 있으므로 빈 줄도 같이 출력된다)

```
while True:
    data = input()
    if not data: break
    print(data)
```
이 코드와 같이 비교하면 이 코드는 키보드를 사용한 입력 방법이고,  
위의 코드는 파일을 사용한 입력 방법이다.

readline() 함수는 문자열을 리턴하고  
첫 줄의 내용을 읽어서 변수에 저장할 수 있는 함수이다.

## readlines 함수 사용하기
readlines 함수는 파일의 모든줄을 읽어서 각각의 줄을 요소로 가지는 리스트를 리턴한다
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'r')
lines = f.readlines()
for line in lines:
    print(line)
f.close()
```
```
1번째 줄 입니다

2번째 줄 입니다

3번째 줄 입니다

4번째 줄 입니다

5번째 줄 입니다

6번째 줄 입니다

7번째 줄 입니다

8번째 줄 입니다

9번째 줄 입니다

10번째 줄 입니다

```
### 줄 바꿈 문자 제거하기
파일을 읽을때 줄바꿈 문자를 제거하고 사용해야 할 경우가 많다.  
strip 함수를 사용하면 줄바꿈 문자를 제거할 수 있다.
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'r')
lines = f.readlines()
for line in lines:
    line = line.strip() # 줄 끝의 줄 바꿈 문자를 제거한다.
    print(line)
f.close()
```
```
1번째 줄 입니다
2번째 줄 입니다
3번째 줄 입니다
4번째 줄 입니다
5번째 줄 입니다
6번째 줄 입니다
7번째 줄 입니다
8번째 줄 입니다
9번째 줄 입니다
10번째 줄 입니다
```

## read 함수 사용하기
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'r')
data = f.read()
print(data)
f.close()
```
f.read()는 파일의 내용 전체를 문자열로 리턴한다  
따라서 위의 data는 파일의 전체 내용이다.  

## 파일 객체를 for 문과 함께 사용하기
파일 객체(f)는 기본적으로 위와 같이 for 문과 함께 사용하여 파일을 줄 단위로 읽을 수 있다.  
```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'r')
data = f.read()
print(data)
f.close()
```

# 파일에 새로운 내용 추가하기
쓰기모드('w')로 파일을 열 때 이미 존재하는 파일을 열면 그 파일의 내용이 모두 사라지게 된다  
하지만 원래 있던 값을 유지하면서, 단지 새로운 값만 추가할 땐  
파일을 추가모드('a')로 열면 된다.

```
f = open("/Users/gwag-yunseong/Documents/새파일.txt",'a')
for i in range(11,20):
    data = "%d번째 줄 입니다\n" %i
    f.write(data)
f.close()
```
```
1번째 줄 입니다
2번째 줄 입니다
3번째 줄 입니다
4번째 줄 입니다
5번째 줄 입니다
6번째 줄 입니다
7번째 줄 입니다
8번째 줄 입니다
9번째 줄 입니다
10번째 줄 입니다
11번째 줄 입니다
12번째 줄 입니다
13번째 줄 입니다
14번째 줄 입니다
15번째 줄 입니다
16번째 줄 입니다
17번째 줄 입니다
18번째 줄 입니다
19번째 줄 입니다
11번째 줄 입니다
12번째 줄 입니다
13번째 줄 입니다
14번째 줄 입니다
15번째 줄 입니다
16번째 줄 입니다
17번째 줄 입니다
18번째 줄 입니다
19번째 줄 입니다
```

# with 문과 함께 사용하기
이떄까지 파일을 열고 닫을때  
open과 close를 같이 사용하여 열고 닫았다  

파일을 열고 닫는것을 자동으로 실행하기 위해서는 with문을 사용하면 된다
```
with open("foo.txt","w") as f:
  f.write("Life is too short")
```
이 처럼 with문을 사용하면 with 블록을 벗어나는 순간 열린 파일 객체 f가 자동을 닫힌다.
