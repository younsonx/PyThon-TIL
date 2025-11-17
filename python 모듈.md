# 모듈
함수나 변수 또는 클래스를 모아놓은 파이썬 파일  
모듈은 다른 파이썬 프로그램에서 불러와 사용할 수 있도록 만든 파이썬 파일이다.  

## 모듈 만들기
```
def add(a, b):
    return a + b

def sub(a, b):
    return a - b
```
위와 같은 코드가 저장된 파일이 바로 모듈이다.

## 모듈 불러오기
터미널에서 내 문서로 이동한 후 파이썬 모듈(파일)을 저장한 디렉터리로 이동한 후 실행해야한다.  
그래야만 대화형 인터프리터에서 파이썬 모듈을 읽을 수 있다  
```
gwag-yunseong@gwag-yunseong-ui-MacBookAir ~ % cd Documents
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % ls
__pycache__		function.py		my_project
add_data.py		funtion_practice.py	newfile.py
argv test.py		game			practice.py
calculator		hello.py		readline_test.py
class_parctice.py	helloWorld.py		review.py
class.py		helloWorld2.py		sys1.py
control.py		json_write_read.py	test.txt
data_TypesQ.py		line_read_process.py	try_except.py
exam.py			log_append.py		write_data.py
example1.txt		logfile.txt		write_read_basic.py
example2.txt		main.py			새파일.txt
example3.json		mod1.py			새파일2.txt
file_in_out_practice.py	modtest.py		실습파일.txt
file.py			multistrings.py
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python 3
zsh: command not found: python
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3
Python 3.13.7 (v3.13.7:bcee1c32211, Aug 14 2025, 19:10:51) [Clang 16.0.0 (clang-1600.0.26.6)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import mod1
>>> print(mod1.add(3,4))
7
>>> print(mod1.sub(3,4))
-1
>>> 
```
여기서 import는 이미 만들어 놓은 파이썬 모듈을 사용할 수 있게 해 주는 명령어 이다.  
import는 현재 디렉터리에 있는 파일이나, 파이썬 라이브러리가 저장된 디렉터리에 있는 모듈만 불러올 수 있다.  

함수를 직접 import하려면 
```
from 모듈이름 import 모듈함수
```
라 작성하면 된다.
```
>>> from mod1 import add
>>> add(3,4)
7
```
그러나 이렇게하면 모듈에 존재하는 함수 하나만 사용할 수 있다. 모듈의 여러 함수를 사용하기 위해서는
```
>>> from mod1 import add, sub
>>> add(3,4)
7
>>> sub(3,4)
-1
```
쉼표로 구분하여 필요한 함수를 불러올 수 있다.
또 다른 방법은 
```
from mod1 import *
```
정규 표현식에서 * 문자는 '모든것'이라는 뜻인데, 파이썬에서도 또한 같은 의미로 사용한다.  
따라서 mod1의 모든 함수를 불러와서 사용한다는 의미이다. 

## if __name__ == "__main__"의 의미
```
def add(a,b):
    return a + b

def sub(a,b):
    return a - b

print(add(1,4))
print(sub(4,2))
```
```
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3 mod1_review.py
5
2
```
예상한 대로 결괏값이 잘 출력된다. 그런데 모듈을 import할 때는 조금 이상한 문제가 생긴다.

```
gwag-yunseong@gwag-yunseong-ui-MacBookAir ~ % cd Documents
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3
Python 3.13.7 (v3.13.7:bcee1c32211, Aug 14 2025, 19:10:51) [Clang 16.0.0 (clang-1600.0.26.6)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import mod1_review
5
2
```
모듈을 import 하는순간 모듈파일이 실행되어 결괏값을 출력한다. 이러한 문제를 방지하려면 다음과 같이 파일을 수정해야한다.

```
def add(a, b):
    return a + b

def sub(a, b):
    return a - b

if __name__ == "__main__":
    print(add(1, 4))
    print(sub(4, 2))
```
```
>>> import mod1_review
>>> 
```

### __name__ 변수란?

파이썬의 __name__ 변수는 파이썬이 내부적으로 사용하는 특별한 변수 이름이다.  
만약 gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3 mod1.py 처럼  
직접 mod1.py 파일을 실행할 경우 __name__ 변수에는 __main__ 값이 저장된다  

하지만 파이썬 셀이나 다른 파이썬 모듈에서 mod1을 import할 경우에는 mod1.py의 __name__ 변수에  
mod1.py의 모듈 이름인 mod1이 저장된다. 

즉 실행벙식에 따라 __name__ 변수에 무엇이 들어갈지 결정된다.  
터미널에서 python3 mod1.py 라 하면 mod1.py 파일을 직접 실행하는것이 되고,  
import mod1 이라하면 mod1.py 파일을 모듈로 불러왔다고 인식된다.
