# 함수

똑같은 내용을 반복해서 사용해야할 때  
반복되는 부분이 있을 경우, '반복적으로 사용되는 가치 있는 부분'을 한 뭉치로 묶어  
어떤 입력값을 주었을때 어떤 결괏값을 리턴해준다 라는 식으로 함수를 작성한다  

함수의 표현식
```
def 함수이름(매개변수):
  ~~~~~~~
```
여기서 매개변수는 함수에 입력으로 전달되는 값을 받는 변수이다.  

## 매개변수와 인수
매개변수 => 함수에 입력으로 전달된 값을 받는 변수    
인수 => 함수를 호출할때 전달하는 입력값을 의미  

```
def add (a, b): #a,b는 매개변수
    return a + b

a = 3
b = 4
c = add(a, b) #3, 4는 인수
print(c)
```

## 입력값과 리턴갑에 따른 함수 형태

### 일반적인 함수
입력값이 있고, 리턴값이 있는 함수가 일반적인 함수
```
def 함수이름(매개변수):
  ~~~~~
  return 리턴값
```
```
def add (a, b):
    result = a + b
    return result # a + b의 결괏값을 리

a = add(3, 4)
print(a)
```
이러한 형태는  
리턴값을 받을 변수 = 함수 이름(입력인수1, 입력인수2, ...)  

### 입력값이 없는 함수
입력값은 없고, 리턴값이 존재하는 함수형태
```
def say():
    return 'Hi'

a = say()
print(a)
```
이 함수를 사용하기 위해선 괄호 안에 아무것도 넣지 않아야 한다  
이 함수는 입력값은 없지만 리턴값으로 Hi라는 문자열을 리턴한다  

이러한 형태는  
리턴값을 받을 변수 = 함수 이름()

### 리턴값이 없는 함수
입력값은 있고, 리턴값이 없는 함수형태
```
def add(a, b):
    print("%d + %d = %d" %(a, b, a+b))

add(3,4)
```
이러한 형태는  
함수이름(입력인수1, 입력인수2, ...)  

print문은 함수의 구성요소 중 하나인 수행할 문장에 해당한다. 따라서 리턴값은 당연히 없다.  
이를 확인하기 위해
```
def add(a, b):
    print("%d + %d = %d" %(a, b, a+b))

a = add(3,4) #add함수의 리턴값을 a에 대입
print(a) #a값 출력
```
```
3 + 4 = 7
None
```

### 입력값도, 리턴값도 없는 함수
```
def say():
  print('Hi')
```
이 함수를 사용하는 방법은 단 한가지 이다
```
say()
```
이러한 형태는  
함수이름()

## 매개변수를 지정하여 호출하기
함수를 호출할떄 매개변수를 지정할 수 있다 즉,  
리턴값을 받을 변수에 매개변수를 지정한다.  
```
def sub (a, b):
    return a - b

result = sub(a = 7, b = 5)
print(result)
```
매개변수 지정을 이용하면 순서에 상관없이 함수를 사용할 수 있다
```
def sub (a, b):
    return a - b

result = sub(b = 6, a = 3)
print(result)
```

## 입력값이 몇 개가 될 지 모를때
입력값이 여러개 일때 매개변수 앞에 '*'를 붙인다.

표현식
```
def 함수 이름(*매개변수):
  ~~~~~~
```
### 여러개의 입력값을 받는 함수 만들기
```
def add_many(*args):
    result = 0
    for i in args:
        result = result + i
    return result

result = add_many(1, 2, 3)
print(result)

result = add_many(1,2,3,4,5,6,7,8,9,10)
print(result)
```
```
6
55
```
매개변수 앞에 *를 붙이면 입력값들을 전부 모아 튜플로 만들어준다  

여러 개의 입력을 처리할 떄 def add_many(*args)처럼 함수의 매개변수로 *args하나만 사용할 수 있는 것은 아니다.  
```
def add_mul(choice, *args):
    if choice == "add":
        result = 0
        for i in args:
            result = result + i
    elif choice == "mul":
        result = 1
        for i in args:
            result = result * i
    return result

result = add_mul('add', 1,2,3,4,5)
print(result)

result = add_mul('mul', 1,2,3,4,5)
print(result)
```
```
15
120
```
## 키워드 매개변수, kwargs
키워드 매개변수를 사용할때는 매개변수 앞에 '**'를 붙인다
```
def key_wargs(**kwargs):
    print(kwargs)

key_wargs(a=1)
key_wargs(name = 'foo', age = 3)
```
함수의 입력값으로 a=1이 사용되면 kwargs는 {'a': 1}이라는 딕셔너리가 되고  
입력값으로 name = 'foo', age = 3이 사용되면 kwargs는 {'name': 'foo', 'age': 3}이라는 딕셔너리가 된다.

## 함수의 리턴값은 언제나 하나이다.
```
def add_and_mul(a, b):
    return a+b, a*b
```
```
def add_and_mul(a, b):
    return a+b, a*b

result = add_and_mul(3, 4)
print(result)
```
2개의 입력 인수를 받아 더한 값과 곱한 값을 리턴하는 함수이다.  
언뜻 보기에 리턴값을 받아들이는 변수는 result 하나만 쓰였으므로 오류가 발생하지 않을까 하지만  
오류가 발생하지 않는다. 그 이유는  
함수의 리턴값은 언제나 1개이다.  
add_and_mul 함수의 리턴값 a+b, a*b는 튜플값 하나인 (a+b, a*b)로 리턴된다.

만약 이 하나의 튜플값을 2개의 값으로 분리하여 받고 싶다면 
```
def add_and_mul(a, b):
    return a+b, a*b

result1, result2 = add_and_mul(3, 4)
print(result1)
print(result2)
```
```
7
12
```
그러면 리턴을 두번 입력하면 동일한 결과가 있지 않을까? 하지만 그렇지 않다.  
함수는 리턴문을 만나는 순간, 리턴값을 돌려 준 다음 함수를 빠져나간다.
```
def add_and_mul(a, b):
  return a + b
  return a * b
```
첫 번째 리턴문을 만나는 순간 함수는 리턴값을 돌려 준 다음 함수를 빠져나간다.

### return 문의 또 다른 쓰임새
return 문을 단독으로 사용하여 함수를 즉시 빠져나갈 수 있다
```
def say_nick(nick):
    if nick == "바보":
        return
    print("나의 별명은 %s 입니다" %nick)

say_nick("야르")
say_nick("바보")
```
이 함수 역시 리턴값이 존재하지 않는다. 문자열을 출력한다는 것과, 리턴값이 있다는 것은 전혀 다른 말이므로 혼동하지말자
```
나의 별명은 야르 입니다 #return문이 실행되지 않고 print문 실핼
 #return문이 실행되어 함수를 빠져나옴
```

## 매개변수에 초깃값 미리 설정하기
```
def say_myself(name, age, man=True):
    print("my name is %s" %name)
    print("i'm %d years old" %age)
    if man:
        print("man")
    else:
        print("gril")

say_myself("youn", 22)
print(' ')
say_myself("youn", 22, True)
```
man = True처럼 매개변수에 미리 값을 넣어 준 것이다. 이것이 함수의 매개변수에 초깃값을 설정하는 방법이다  
say_myself 함수는 위의 두가지 방법처럼 사용할 수 있는데  
첫 번쨰 방법에서는 man이라는 변수에 입력값을 주지 않았지만, man은 초깃값으로 True를 갖게 되므로 동일한 결괏값을 가지게 된다

```
def say_myself(name, age, man=True):
    print("my name is %s" %name)
    print("i'm %d years old" %age)
    if man:
        print("man")
    else:
        print("gril")

say_myself("youn", 22)
print(say_myself)
```
함수를 호출하는것과 print문을 이용하여 출력하는것에 주의하자.  

chatGPT
```
파이썬에서 함수도 하나의 객체(값) 입니다.
그래서 say_myself는 "함수 객체(function object)"를 가리키고,
print()는 그 객체의 기본 표현(Representation)을 출력해요.

<function say_myself at 0x103a18c20>

say_myself("youn", 22)
이건 함수 호출(call) 이에요.
즉, 괄호 () 를 붙이면 실제로 실행됩니다.
```
또한 초기화 하고싶은 매개변수는 항상 뒤쪽에 놓아야 한다. 그렇지 않으면 오류가 발생한다.
```
def say_myself(name, man=Trur, age)
```
라 하면 초깃값이 없는 매개변수는 초깃값이 있는 매개변수 뒤에 사용할 수 없다 라는 오류가 출력된다

## 함수 안에서 선언한 변수의 효력 범위
함수 안에서 선언한 변수는 함수 내에서만 영향을 미친다.  
입력값을 전달 받는 매개변수는 함수 안에서만 사용하는 변수일 뿐, 함수 밖의 변수와는 전혀 상관없다

```
a = 1
def vartest(a):
    a = a + 1

vartest(a)
print(a)
```
전역변수 a의 값 1이 함수의 매개변수 a로 복사되어 전달 됨.  
즉, 함수 안에서만 쓰이는 지역변수 a가 새로 생긴다.
```
def vartest(a): 
    a = a + 1

vartest(3)
print(a)
```
```
Traceback (most recent call last):
  File "/Users/gwag-yunseong/Documents/function.py", line 5, in <module>
    print(a)
NameError: name 'a' is not defined
```
함수 밖에서 사용한 변수 a는 어디에도 선언되지 않았다. 따라서 오류가 발생한다.  
4를 출력하기 위해선  
```
def vartest(a): 
    a = a + 1
    print(a)

vartest(3)
```
라 하면 된다.

## 함수 안에서 함수 밖의 변수를 변경하는 방법

### return 사용하기
```
a = 1
def vartest(a):
    a = a + 1
    return a

a = vartest(a)
print(a)
```
vartest 함수는 입력으로 들어온 값에 1을 더한 값을 리턴하도록 변경했다.  
a = vartest(a)라고 작성하면 a에는 vartest 함수의 리턴값이 대입된다.  
물론 a변수는 함수 내부와 함수 외부와 서로 다르다.

### global 명령어 사용하기
global 명령어는 함수 밖의 변수를 직접 사용하겠다는 뜻 이다.  
그러나 함수는 독립적으로 존재하는것이 좋고, 외부 변수에 종속되는 함수는 그다지 좋은 함수가 아니므로 리턴문을 사용하자
```
a = 1

def vartest():
    global a
    a = a + 1

vartest()
print(a)
```

## lambda 예약어
lambda는 함수를 생성할때 쓰는 예약어로, def와 동일한 목적으로 사용되지만  
함수를 한 줄로 간결하게 만들때 사용된다

표현식
```
함수 이름 = lambda 매개변수1, 매개변수2, ... : 매개변수를 이용한 표현식
```
```
add = lambda a, b: a+b
result = add(3, 4)
print(result)
```




























