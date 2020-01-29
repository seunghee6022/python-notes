# Jupyter Notebook

2020.01.20

***

`ctrl`+`enter` : 현재 셀을 실행하고 실행 후 현재 셀 선택(머무름)

`alt` +`enter` : 현재 셀을 실행하고 밑에 새로운 셀 추가한다

`shift`+`enter` :  현재 셀을 실행하고 다음 셀로 이동한다

마크다운으로 셀을 선택 후 글 쓰고 `shift`+`enter`  하면 마크다운 됨. 

`Help` > `Keyboard Shortcuts`  : 단축키 알 수 있다.

`a` : command line 에서 누르면 위에 셀 생김

`b` : command line 에서 누르면 밑에 셀 생김

***

![01_python_intro.ipynb 로딩](C:\Users\multicampus\Desktop\Markdown 필기\1.PNG)

***

###  PEP-8 파이썬에서 권장하는 코딩 rule

https://www.python.org/dev/peps/pep-0008/

***

### docstring 

mysum.__**doc**__

```
docstring은 """으로 표현한다. 
여러 줄의 주석을 작성할 수 있으며, 보통 함수/클래스 선언 다음에 해당하는 설명을 위해 활용한다.
```

```python
#
# 이 줄은 실행되지 않습니다.
def mysum(a, b):  # 함수 로출에서의 콤마와 콜론의 띄어쓰기 rule.
    """
    이것은 덧셈 함수입니다.
    이줄은 실행되지 않아요.
    다만 왜 docstring이라고 
    불리는지 이유가 있습니다.

    """
    print(a + b) #괄호 안 인자를 적을 때는 인자랑 괄호를 띄우지 x rule.
```

```python
# docstring은 다음과 같이 확인할 수 있습니다.
mysum.__doc__
```

결과

```python
Out[9]:
'\n    이것은 덧셈 함수입니다.\n    이줄은 실행되지 않아요.\n    다만 왜 docstring이라고 \n    불리는지 이유가 있습니다.\n\n    '
```



### ; 사용

한 줄로 표기할 떄는 ;를 작성하여 표기할 수 있다. 

```python
print('hello'); print('world')
hello
world
```

다음 라인에서도 코드가 계속 이어지려면?    `\`    (가독성 높임)

```python
print('\
      ssafy')
```

__but [] {} ()는 \ 없이도 가능하다.__

```python
lunch=[
    '짜장면', '짬뽕', '탕수육',
    '군만두', '물만두']
print(lunch)

Out[21]:
['짜장면', '짬뽕', '탕수육', '군만두', '물만두']
```



### 같은/다른 값 동시에 할당 가능

```python
1. 같은 값 동시 할당
x = y = 1004
print(x,y)

Out[22]:
1004 1004

2.다른 값 동시 할당
x, y= 'ssafy', 5
print(x,y)

Out[22]:
ssafy 5
```



### 서로 값을 동시에 바꾸고 싶을 때

```python
x, y = y, x
print(x,y)

Out[22]:
5 ssafy
```



### 숫자 type

* 8진수 0o

* 2진수 0b

* 16진수 0x

![](C:\Users\multicampus\Desktop\Markdown 필기\3-1579502914021.PNG)



#### Arbitary-precision arithmetic



![](C:\Users\multicampus\Desktop\Markdown 필기\1-1579502658950.PNG)



### 실수

* 컴퓨터식 지수 표현 방식 e

```python
b = 314e-2 #314 * 10**-2 = 314*0.01
type(b)
print(b)

Out[40]:
float
3.14
```

* 컴퓨터의 숫자 표현 2진 방식의 오류

```
3.5 - 3.12

Out[41]:
0.3799999999999999
```

* 해결 방법 round사용

```
round(3.5 - 3.12, 2)

Out[43]:
0.38
```

* 처리 방법

  * 기본적 처리 방법

  ```python
  a = 3.5 - 3.12
  b = 0.38
  abs(a - b) <= 1e-10 :둘의 차이가 매우 작은지를 확인
      
  Out[44]:
  True
  ```

  * sys 모듈 사용

  ```python
  import sys
  abs(a - b) <= sys.float_info.epsilon
  
  Out[45]:
  True
  ```

  * math 모듈 활용

  ```python
  import math
  math.isclose(a,b)
  
  Out[46]:
  True
  ```



***



### 복소수 Complex numbers

z.real(z의 실수부) , z.imag(z의 허수부) 사용

허수부를 j로 표현

켤레복소수 z.conjugate()

```python
a = 3-4j
type(a)
print(a.real)
print(a.imag)
print(a.conjugate())

Out[47]:
complex
3.0
-4.0
(3+4j)
```

* 문자열을 복소수로 변환(부호 앞뒤로 공백 있으면 안된다. 꼭 복소수의 형태여야)

```python
s = '1+2j'
type(s)
complex(s)

Out[49]:
str
(1+2j)
```

```python
b = '1 + 2j'  #복소수의 형태 파괴!!!!!!!!!!!!
type(b)
complex(b)

Out[49]:
str
에러남
```



### bool

파이썬에는 True와 False로 이뤄진 bool 타입이 있습니다.
비교/논리 연산을 수행 등에서 활용됩니다.
다음은 False로 변환됩니다.
0, 0.0, (), [], {}, '', None

* bool(0) : False
* bool(1) : True
* bool(None) : False
* bool([]) : False
* bool(' ') : False  #빈 문자열 false
* bool('hi') : True



### None

파이썬에서는 값이 없음을 표현하기 위해 None 타입이 존재

* type(None) : NoneType



### String

__기본 활용법__

* 문자열은 Single quotes(')나 Double quotes(")을 활용하여 표현 가능하다.
  * 작은따옴표: '"큰" 따옴표를 담을 수 있습니다'
  * 큰따옴표: "'작은' 따옴표를 담을 수 있습니다"
  * 삼중 따옴표: '''세 개의 작은따옴표''', """세 개의 큰따옴표"""
* 단, 문자열을 묶을 때 동일한 문장부호를 활용해야하며, PEP-8에서는 하나의 문장부호를 선택하여 유지하도록 하고 있다. (Pick a rule and Stick to it)
* 사용자에게 받은 입력은 기본적으로 str입니다.
* 따옴표 사용
  문자열 안에 문장부호(', ")가 사용될 경우 이스케이프 문자(\)를 활용 가능 합니다. 

```
print('철수가 말했다."안녕?"')
print('철수가 말했다.\'안녕?\'')


철수가 말했다."안녕?"
철수가 말했다.'안녕?'
```

* 여러줄 출력

```
print("""
개행문자 없이
여러줄을 그대로 출력 가능합니다.
""")

개행문자 없이
여러줄을 그대로 출력 가능합니다.
```

* 문자열은 + 연산자로 이어붙이고, * 연산자로 반복시킬 수 있습니다.

```python
3*'hi' + 'hello'
Out[79]:
'hihihihello'
```



* 두 개 이상의 문자열이 연속해서 나타나면 자동으로 이어 붙여집니다.

```python
'Py' 'th' 'on'

Out[81]:
'Python'
```



### 이스케이프 시퀀스

![image-20200120164901226](C:\Users\multicampus\Desktop\Markdown 필기\image-20200120164901226.png)

```python
print('이 다음은 엔터. \n tab\ttab')

print('내용을 옆으로 띄어서 출력하고 싶으면?', end='\t')
print('옆으로 띄워짐',end='\n')
print('내용을 다음줄으로 띄어서 출력하고 싶으면?', end='\n')
print('다음줄로 띄워짐')

print('개행문자 말고도 가능합니다.', end='!')
print('진짜로', end='!!\n')
print('알고보면 print는 기본이 \\n', end='!')

이 다음은 엔터. 
 tab	tab
    
내용을 옆으로 띄어서 출력하고 싶으면?	옆으로 띄워짐
내용을 다음줄으로 띄어서 출력하고 싶으면?
다음줄로 띄워짐

개행문자 말고도 가능합니다.!진짜로!!
알고보면 print는 기본이 \n!

```



### String interpolation

* %-formatting 

```
name = 'Jeong'
print('Hello, %s')
```

* str.format()  - 숫자로 위치 설정도 가능

```python
print('Hello, {}'.format(name))
print(f'Hello, {1},{0}'.format(name,'sh')) #숫자로 위치 설정 가능
```

* f-strings : 파이썬 3.6 이후 버전에서 지원("""도 활용 가능)

```python
print(f'Hello, {name}')
print(f"""
Hello,
{name}
""")
```

* f-strings에서는 형식을 지정할 수 있다.

```python
import datetime
#from datetime import datetime
today = datetime.datetime.now()
print(today)

2020-01-20 17:41:03.276839
```

```python
print(f"오늘은 {today :%Y}년 {today:%m} 월 {today: %d}일 {today: %A}")

오늘은 2020년 01 월  20일  Monday
```

* f-strings에서는 연산과 출력형식 지정도 가능하다.  ( {pi: .4} 소수점 4째자리까지 지정 )

```python
pi = 3.141592
print(f'원주율은 {pi:.4} 반지름이 2일 때 원의 넓이는 {pi*2*2}')


원주율은 3.142 반지름이 2일 때 원의 넓이는 12.566368
```

