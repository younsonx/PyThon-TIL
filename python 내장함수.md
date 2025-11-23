### abs(x)       
x의 절댓값 리턴 함수  
```
abs(-3)
3
```

### all(x)
반복가능한 데이터x를 입력값으로 받으며, x의 요소가 모두 참이면 True, 하나라도 거짓이면 False 리턴
```
all([1,2,3])
True

all([1,2,3,0])
False
```

### any(x)
반복가능한 데이터 x를 입력값으로 받으며, x의 요소가 하나라도 참이면 True, 모두 거짓이면 False 리턴
```
any([1,0])
True

any([0, ""])
False
```

### chr(i)
유니코드 숫자 값을 입력받아, 그 코드에 해당하는 문자를 리턴하는 함수
```
chr(97)
'a'
```

### dir()
객체가 지는 변수나 함수를 보여주는 함수.  
다음의 예시는 리스트가 가진 함수(메서드)를 보여주는 예이다. 
```
dir([1,2,3])
['__add__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getstate__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

### divmod(a, b)
2개의 숫자를 입력으로 받아 a를 b로 나눈 몫과 나머지를 튜플로 리턴한다.
```
divmod(7,3)
(2, 1)
```

### enumerate
열거하다 라는 뜻이며, 순서가 있는 데이터(리스트, 튜플, 문자열)를 입력으로 받아  
인덱스 값을 포함하는 enumerate 객체를 리턴한다.
```
for i, name in enumerate(['body', 'foo', 'bar']):
    print(i, name)

    
0 body
1 foo
2 bar
```

### eval(expression)
문자열로 구성된 표현식을 입력으로 받아 해당 문자열을 실행한 결괏값을 리턴하는 함수이다. 
```
eval('1 + 2')
3

eval("'hi' + 'a'")
'hia'

eval('divmod(4,3)')
(1, 1)
```

### filter
무엇인가를 걸러낸다 라는 뜻으로  
```
filter(함수, 반복 가능한 데이터)
```
첫번째 인수로 함수, 두번째 인수로 그 함수에 차례대로 들어갈 반복가능한 데이터를 받는다.  
그리고 그 반복가능한 데이터의 요소 순서대로 함수를 호출했을 때 리턴값이 참인 것만 묶어서 리턴한다.

```
def positive(x):
    return x > 0

print(list(filter(positive, [1,2,-3,0,-5,6])))
```
```
[1, 2, 6]
```

filter(positive, [1,2,-3,0,-5,6])은 리스트의 각 요솟값을 순서대로  
positive 함수에 적용하여 리턴값이 참인 것만 묶어서 리턴한다.

위의 예제에서 filter를 사용하지 않고 코드를 작성하려면
```
def positive(l):
    result = []
    for i in l:
        if i > 0:
            result.append(i)
    return result

print(positive([1,2,-3,0,-5,6]))
```

이 예제에 lambda를 사용하면 더욱 간단해진다.
```
list(filter(lambda x: x>0, [1,2,-3,0,-5,6]))
[1, 2, 6]
```

### hex(x)
정수를 입력받아 16진수 문자열로 변환하여 리턴하는 함수
```
hex(234)
'0xea'

hex(3)
'0x3'
```

### id
객체를 입력받아 객체의 고유 주솟값(레퍼런스)을 리턴하는 함수이다.
```
a = 3
id(3)
4335364600
id(a)
4335364600
b = a
id(b)
4335364600
```
모두가 같은 객체를 가리키고 있다. 

만약 id(4)라고 입력하면 4와는 다른 객체 이므로 다른 주솟값이 출력되는건 자명하다.

### input([prompt])
사용자 입력을 받는 함수이다. 입력 인수로 문자열을 전달하면, 그 문자열은 프롬프트가 된다  
```
a = input() # 사용자가 입력한 정보를 변수 a에 저장
hi # hi 입력
a
'hi' # 사용자 입력으로 받은 'hi' 출력
```

문자열이 프롬프트가 되는 예시
```
b = input("Enter: ") # 입력인수로 "Enter: " 문자열 전달
Enter: hi # Enter 프롬프트를 띄우고 사용자 입력을 받음
b
'hi' # 사용자 입력으로 받은 'hi' 출력
```

### int(x)
문자열 형태의 숫자나, 소수점이 있는 숫자를 정수로 리턴하는 함수이다. 만약 정수가 입력되면 그대로 리턴한다.
```
int(3)
3
int(3.4)
3
```

**int(x, radix)** 는 radix진수로 표현된 문자열 x를 10진수로 변환하여 리턴한다  
예로 2진수로 표현된 '11'의 10진수 값은 다음과 같이 구할 수 있다.  
```
int('11', 2)
3
```
16진수로 표현된 '1A'의 10진수 값은 다음과 같이 구한다. 
```
int('1A', 16)
26
```

### isinstance(object, class)
isinstance 함수는 첫 번쨰 인수로 객체, 두 번째 인수로 클래스를 받는다.  
입력으로 받은 객체가 클래스의 인스턴스인지를 판단하여 참, 거짓을 리턴한다. 
```
class Person: pass # 아무런 기능이 없는 Person 클래스 생성

a = Person() # Person 클래스의 인스턴스 a 생성
isinstance(a, Person) # a가 Person 클래스의 인스턴스인지 확인
True
```
a 객체가 Person 클래스의 인스턴스라는것을 확인 시켜준다. 

```
b = 3
isinstance(b, Person)
False
```
b는 Person 클래스의 인스턴스가 아니라는것을 확인 시켜준다

### len()
입력값의 길이를 리턴하는 함수
```
len('kwakyounseong')
13
```

### list()
반복가능한 데이터를 입력으로 받아 리스트로 만들어 리턴하는 함수
```
list('younseong')
['y', 'o', 'u', 'n', 's', 'e', 'o', 'n', 'g']

list((1,2,3))
[1, 2, 3]
```

### map(f, iterable)
함수(f)와 반복 가능한 데이터를 입력으로 받는다.  
map은 입력받은 데이터의 각 요소에 함수 f를 적용한 결과를 리턴하는 함수이다.
```
def two_times(x):
    return x*2

print(list(map(two_times, [1,2,3,4])))
```
```
[2, 4, 6, 8]
```

이 예제를 map 함수를 사용하지 않고 구현 하려면

```
def two_times(numberlist):
    result = []
    for number in numberlist:
        result.append(number*2)
    return result

result = two_times([1,2,3,4])
print(result)
```

위의 예제 또한 lambda 예약어를 사용하면 간략하게 만들 수 있다.
```
list(map(lambda x: x*2, [1,2,3,4]))
[2, 4, 6, 8]
```

### max(iterable)
인수로 반복 가능한 데이터를 입력받아 그 최댓값을 리턴하는 함수.
```
max([1,2,3])
3

max("python") # 문자열의 경우, 유니코드의 값이 가장 큰 문자를 리턴
'y' 
```

### min(iterable)
max와 정확히 반대로, 최솟값을 리턴하는 함수.
```
min([1,2,3])
1

min("python")
'h'
```

### oct(x)
정수를 8진수 문자열로 바꾸어 리턴하는 함수
```
oct(10)
'0o12'
```

### open(filename, [mode])
파일 이름과 읽기 방법을 입력받아 파일 객체를 리턴하는 함수  
읽기 방법(mode)을 생략하면 기본값인 읽기 모드(r)로 파일 객체를 만들어 리턴한다

읽는 방법에는 w, r, a, b가 있고, 순서대로  
쓰기모드로 파일 열기, 읽기모드로 파일 열기, 추가모드로 파일 열기, 바이너리 모드로 파일 열기를 의미한다.   
b는 w,r,a와 함께 사용한다.
```
f = open("binary_file", "rb")
```

### ord(c)
문자의 유니코드 숫자 값을 리턴하는 함수
```
ord('a')
97
```

### pow(x, y)
x를 y제곱한 결과값을 리턴하는 함수.
```
pow(2,4)
16
```

### range([start,] stop [,step])
입력받은 숫자에 해당하는 범위 값을 반복 가능한 객체로 만들어 리턴한다. 

#### 인수가 하나일 경우
시작숫자를 정해주지 않으면, range함수는 0부터 시작한다. 
```
list(range(5))
[0, 1, 2, 3, 4]
```

#### 안수가 2개일 경우
입력으로 주어지는 2개의 인수는 시작 숫자와, 끝 숫자로 이루어진다.  
단 끝 숫자는 해당범위에 포함되지 않는다. 
```
list(range(5, 10))
[5, 6, 7, 8, 9]
```

#### 인수가 3개일 경우
세 번째 인수는 숫자 사이의 거리를 나타낸다. 
```
list(range(1,10,2)) # 1부터 9까지, 숫자 사이의 거리는 2
[1, 3, 5, 7, 9]
```

### round(number[,ndigits])
숫자를 입력받아 반올림해 리턴하는 함수.
```
round(4.6)
5
```
```
round(5.234, 2)
5.23
```
round 함수의 두 번째 인수는 반올림하여 표시하고 싶은 소수점의 자릿수를 의미한다.

### sorted(iterable)
입력 데이터를 정렬한 후 그 결과를 리스트로 리턴하는 함수이다.  
리스트 자료형에도 sort 함수가 있지만  
리스트 자료형의 sort 함수는 리스트 객체 그 자체를 정렬할 뿐, 정렬된 결과를 리턴하지는 않는다. 
```
sorted([1,3,2])
[1, 2, 3]
```

### str(object)
문자열 형태로 객체를 변환하여 리턴하는 함수이다.  
```
str(3)
'3'
```

```
type(str(3))
<class 'str'>
```

### sum(iterable)
입력 데이터의 합을 리턴하는 함수
```
sum([1,3,4])
8
```

### tuple(iterable)
반복 가능한 데이터를 튜플로 바꾸어 리턴하는 함수이다.  
만약 입력값이 튜플인 경우에는 그대로 유지된다.
```
tuple("abc")
('a', 'b', 'c')
tuple([1,2,3])
(1, 2, 3)
tuple((1,2,3))
(1, 2, 3)
```

### type(odject)
입력값의 자료형이 무엇인지 알려주는 함수

### zip(*iterable)
동일한 개수로 이루어진 데이터들을 묶어서 리턴하는 함수
```
list(zip([1,2,3], [4,5,6]))
[(1, 4), (2, 5), (3, 6)]
```























