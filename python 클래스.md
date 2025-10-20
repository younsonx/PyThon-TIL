# 클래스

```
class Calculator:
    def __init__(self):
        self.result = 0

   def add(self, num):
       self.result += num
       return self.result

cal1 = Calculator()
cal2 = Calculator()

print(cal1.add(3))  # cal1.result = 0 + 3 → 3
print(cal1.add(4))  # cal1.result = 3 + 4 → 7
print(cal2.add(3))  # cal2.result = 0 + 3 → 3
print(cal2.add(7))  # cal2.result = 3 + 7 → 10
```

calculator 클래스로 만든 별개의 계산기 cal1, cal2가 각각의 역할을 수행한다  
파이썬에선 이것을 객체라 부른다  
이렇게 클래스를 사용하면 계산기의 대수가 늘어나도 객체를 생성만 하면 되므로  
함수만 사용할 때보다 간단하게 프로그램을 작성할 수 있다.

# 클래스와 객체

클래스는 붕어빵 틀  
객체는 붕어빵 이라고 생각하면 된다  

즉 클래스란 똑같은 무언가를 계속 만들어 낼 수 있는 설계도면, 객체는 클래스로 만든 피조물을 뜻한다.  
동일한 클래스로 만들어진 객체들은 서로 영향을 주지 않는다.

```
class Cookie:
    pass
```
이는 클래스의 가장 간단한 예시 이다  
위에서 작성한 클래스는 아무런 기능도 가지고 있지 않은 껍질뿐인 클래스이다.  
하지만 이런 껍질뿐인 클래스도 객체를 생성하는 기능이 있다.

객체를 만들기 위해서는
```
a = Cookie()
b = Cookie()
```
Cookie()의 결괏값을 리턴받은 a와b가 바로 객체이다.

## 객체와 인스턴스의 차이

인스턴스 : 클래스로 만든 객체  

'a는 객체', 'a는 Cookie의 인스턴스'

# 사칙연산 클래스 만들기

클래스는 무작정 만드는 것보다 클래스로 만든 객체를 중심으로 어떤 식으로 동작하게 할 지 미리 구상한 후 생각한 것을  
하나씩 완성해 만들어 나가면 좋다

먼저 a = Fourcal()를 입력해서 a라는 객체를 만든다.  
그런다음 a.setdata(4, 2)를 입력해서 숫자 4와 2를 a에 지정해준다.  
a.add()를 수행하면 두 수를 합한 결과를 리턴한다.  

따라서 만들어진 코드는
```
class FourCal:
    def setdata(self, first, second):
        self.first = first
        self.second = second

    def add(self):
        result = self.first + self.second
        return result

    def mul(self):
        result = self.first * self.second
        return result

    def sub(self):
        result = self.first - self.second
        return result

    def div(self):
        result = self.first / self.second
        return result
```
하나씩 살펴보면  

우선 클래스 내에 함수를 구현하는것을 **메서드**라 부른다.  
setdata 메서드를 다시 보면
```
def setdata(self, first, second):
        self.first = first
        self.second = second
```
setdata 메서드에는 총 3개의 매개변수로 self, first, second 3개의 입력값을 받는다 그러나  
setdata 메서드를 호출할때는 a.setdata(4, 2)처럼 두개의 값만 전달된다.  
이는 self에 객체 a가 자동으로 전달되고 나머지 매개변수에 값이 전달되는 형태이다.  

파이썬 메서드의 첫 번째 매개변수 이름은 일반적으로 self를 사용한다.  
객체를 호출할 때 호출한 객체 자신이 전달되기 때문에 self라는 이름을 사용한 것이다.  

```
a = FourCal()
b = FourCal()

a.setdata(4, 2)
a.first() # 4

b.setdata(3, 7)
b.first() # 3
```
확인할 수 있듯이 클래스로 만든 객체의 객체변수는 다른 객체의 객체변수에 상관없이 독립적인 값을 유지한다.

더하기 함수 코드를 살펴보면
```
def add(self):
        result = self.first + self.second
        return result
```
add 메서드의 매개변수는 self, 리턴값은 result이다.  
result는 다음과 같이
```
result = self.first + self.second
```
이다.  
a객체에 의해 add 메서드가 수행되면 add 메서드의 self에는 객체 a가 자동으로 입력되므로
```
result = a.first + a.second
```
로 해석된다

# 생성자
위의 FoulCal 클래스를 다음과 같이 사용하면 에러가 발생한다.
```
a = FourCal()
a.add()
Traceback (most recent call last):
  File "<pyshell#30>", line 1, in <module>
    a.add()
  File "/Users/gwag-yunseong/Documents/class.py", line 7, in add
    result = self.first + self.second
AttributeError: 'FourCal' object has no attribute 'first'
```
setdata 메서드를 수행해야 객체a의 객체변수 first와 second가 생성되기 때문이다.  
이렇게 객체에 first, second와 같은 초깃값을 설정해야 할 필요가 있을때는 생성자를 구현하는것이 안전한 방법이다.  

파이썬 메서드명으로
```
__init__
```
을 사용하면 이 메서드는 생성자가 된다.
```
class FourCal:
    def __init__(self, first, second):
        self.first = first
        self.second = second
    
    def setdata(self, first, second):
        self.first = first
        self.second = second

    def add(self):
        result = self.first + self.second
        return result

    def mul(self):
        result = self.first * self.second
        return result

    def sub(self):
        result = self.first - self.second
        return result

    def div(self):
        result = self.first / self.second
        return result
```
```
def __init__(self, first, second):
        self.first = first
        self.second = second
```
__init__ 메서드는 setdata 메서드와 이름만 다르고 모든 게 동일하다.  
단 메서드 이름을 __init__으로 했기 때문에 생성자로 인식되어 객체가 생성되는 시점에 자동으로 호출된다.
```
a = FourCal(4, 2)
```
라 하면 first와 second에 값을 전달하여 객체가 생성된다.

## __init__ 메서드와 setdata 메서드의 비교
메서드의 역할은 동일하다  
=> 객체의 속성(self.first, self.second)을 초기화(저장)한다.

그러나 전자는 인스턴스가 만들어질 때 자동으로 실행되고,  
후자는 객체를 생성한 후 메서드를 호출해야 한다.

또한 전자는 객체가 처음 만들어질때만 실행되지만,  
후자는 나중에 값을 변경할 수 있다.

따라서 초깃값을 __init__으로 설정해도 객체변수의 값을 setdata 메서드로 변경할 수 있다.
```
a = FourCal(4, 2)
print(a.add())   # 👉 6

a.setdata(10, 5)
print(a.add())   # 👉 15
```

이렇게 하면 a의 객체에 원래 있던 값, (4, 2)가 setdata에 의해 (10, 5)로 덮여쓰여지게 된다.

메모리 관점에서 보면  
a라는 객체는 그대로 존재하지만  
그 객체 내부의 변수값이 바뀐것 이다.
```
초기값: 4 2
객체 id: 4375682816
first 변수 id: 4369110288
second 변수 id: 4369110224

값 변경 후: 10 5
객체 id: 4375682816
first 변수 id: 4369110496
second 변수 id: 4369110432
```
객체의 메모리 주소값은 그대로지만  
객체 내부 변수의 메모리 주소값은 변경된 걸 확인할 수 있다.


| 메서드          | 호출 시점      | 호출 방식 | 역할     |
| ------------ | ---------- | ----- | ------ |
| `__init__()` | 객체 생성 시 1회 | 자동 실행 | 초기값 설정 |
| `setdata()`  | 객체 생성 후    | 직접 호출 | 값 변경   |

| 상황                      | 어떤 방식이 적절한가              |
| ----------------------- | ------------------------ |
| 객체를 만들 때 바로 값 설정        | ✅ `__init__` 사용          |
| 이미 만든 객체의 값을 나중에 바꾸고 싶음 | ✅ `setdata` 같은 별도 메서드 사용 |
| 단순한 계산기처럼 재사용할 필요가 없음   | ❌ `setdata`는 불필요         |

# 클래스의 상속
기존 클래스를 변경하지 않고 기능을 추가하거나 기존 기능을 변경하려고 할 떄 사용한다.  
클래스를 상속하기 위한 표현식은  
```
class 클래스_이름(상속할_클래스의_이름)
```
기존의 FourCal()클래스에 제곱 계산을 하는 클래스를 추가할 때의 예시이다.
```
class MoreFourCal(FourCal):
    def pow(self):
        result = self.first ** self.second
        return result
```

# 메서드 오버라이딩
이제 다음과 같이 실행해보면 아래와 같은 오류를 만나게 될 것이다.
```
a = FourCal(4, 0)
a.div()
Traceback (most recent call last):
  File "<pyshell#43>", line 1, in <module>
    a.div()
  File "/Users/gwag-yunseong/Documents/class.py", line 23, in div
    result = self.first / self.second
ZeroDivisionError: division by zero
```
0으로 나눌때 오류가 아닌 값 0을 리턴받고 싶다면 메서드 오버라이딩을 사용하면 된다.  

메서드 오버라이딩이란 부모클래스(상속한클래스)에 있는 매서드를 동일한 이름으로 다시 만드는 것을 뜻 한다.

```
class SafeFourCal(FourCal):
    def div(self):
        if self.second == 0:
            return 0
        else:
            return self.first / self.second
```
이제 FourCal() 클래스 대신 SafeFourCal() 클래스를 사용해보자
```
a = SafeFourCal(4, 0)
a.div()
0
```
# 클래스 변수
클래스 변수는 객체변수와 달리 클래스로 만든 모든 객체에 공유된다는 특징이 있다.  
클래스 변수의 선언은 다음과 같이 할 수 있다
```
class family:
    lastname = "kim"
```
클래스 변수는 
```
family.lastname
"kim"
```
**클래스_이름.클래스변수**로 사용할 수 있다
```
Family.lastname
'kim'
a = Family()
b = Family()
a.lastname
'kim'
b.lastname
'kim'
Family.lastname = 'park'
a.lastname
'park'
b.lastname
'park'
```
이 예시를 참고하면 클래스변수는 클래스로 만든 모든 객체에 공유된다는 것을 확인할 수 있다.  

## 클래스변수와 동일한 객체변수를 생성

```
class family:
    lastname = 'kwak'

family.lastname
'kwak'

a = family()
b = family()

a.lastname
'kwak'
b.lastname
'kwak'

a.lastname = 'youn'
a.lastname
'youn'
b.lastname
'kwak'
```

이렇게 하면 family클래스의 lastname이 바뀌는 것이 아니라  
a 객체에 lastname이라는 객체변수가 새롭게 생성된다. 즉 객체변수는 클래스변수와 동일한 이름으로 생성할 수 있다.

이것을 메모리 관점에서 보면
```
클래스 변수는 클래스 메모리 영역에 한 번만 저장됨
인스턴스는 그걸 공유해서 참조
인스턴스에 같은 이름의 변수를 만들면,
그때부터는 클래스 변수 참조를 끊고 자기 메모리를 사용함
```







