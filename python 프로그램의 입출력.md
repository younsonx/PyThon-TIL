# sys 모듈 사용하기
sys 모듈을 사용하여 프로그램에 인수를 전달할 수 있다.  
sys 모듈을 사용하려면 import 명령어를 사용해야 한다.  
```
import sys

args = sys.argv[1:]
for i in args:
    print(i)
```
```
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3 sys1.py aaa bbb ccc
aaa
bbb
ccc
```
sys 모듈의 argv는 프로그램 실행 시 전달된 인수를 의미한다.  
따라서 argv[0]은 파일이름 sys1.py가 되고  
argv[1] 부터는 뒤에 따라오는 인수가 차례대로 argv의 요소가 된다  

```
import sys

args = sys.argv[1:]
for i in args:
    print(i.upper(), end=' ')
```
```
gwag-yunseong@gwag-yunseong-ui-MacBookAir Documents % python3 sys1.py life is too short, you need python
LIFE IS TOO SHORT, YOU NEED PYTHON
```

## argv의 심화

sys.argv는 파이썬이 미리 정해놓은 특별한 변수(리스트)이다.  

argv는 프로그램 실행 시 전달되는 인자들을 담고있는 리스트 이다.

### argv 기본 구조
```
sys.argv = [실행한_파일명, 첫번째_인자, 두번째_인자, 세번째_인자, ...]
```

sys.argv[1:]를 자주사용하는 이유는 argv[0] 에는 '실행할 파일 이름'이 들어있다  
따라서 실제 입력값을 처리할때는 [1:]를 자주 쓴다  
하지만 프로그램의 이름이나 실행 경로를 로그로 남기거나, 실행 파일 이름을 자동을 표시해야 할 때는 argv[0]이 필요하다.
```
import sys
print(f"이 프로그램 이름은 {sys.argv[0]} 입니다.")
```
```
이 프로그램 이름은 test.py 입니다.
```
즉 argv[0]은 항상 프로그램 자기 자신을 나타내는 정보이다.










