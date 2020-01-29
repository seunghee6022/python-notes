# Python_chap3_01

20.01.22

***

## Function 함수



### parameter(매개변수) & argument(인자, 전달인자)

> def func(__x__)  x: 매개변수
>
> func(__2__)         2 : 인자 argument

#### parameter

def func(x):
 return x + 2
x 는 매개변수
함수의 정의 부분에서 볼 수 있다.

#### rgument

func(2)
2 는 인자
함수를 호출하는 부분에서 볼 수 있다.



***

<img src="https://user-images.githubusercontent.com/18046097/61181741-2984fd80-a665-11e9-93b8-578c56689d0e.png" alt="programming principle" style="zoom:50%;" />



<img src="https://user-images.githubusercontent.com/18046097/61181750-2ab62a80-a665-11e9-84f3-c2445c098a18.png" alt="programming principle" style="zoom: 33%;" />

***

__YAGNI : You ain't gonna need it ->쓸데없는거 미리 만들지마라 야근한다.__

***



### 함수의 선언과 호출

* 함수 선언은 def로 시작하여 :으로 끝나고, 다음은 4spaces 들여쓰기로 코드 블록을 만든다.
* 함수는 매개변수(parameter)를 넘겨줄 수도 있다.
* 함수는 동작후에 return을 통해 결과값을 전달 할 수도 있다. (return 값이 없으면, None을 반환한다.)
* 함수는 호출을 func() / func(val1, val2)와 같이 한다.

> 활용법
> def func(parameter1, parameter2):
>     code line1
>     code line2
>     return value

<img src="https://user-images.githubusercontent.com/18046097/61181742-2984fd80-a665-11e9-9d5c-c90e8c64953e.png" alt="function descrpition" style="zoom:70%;" />

```python
#사각형 코드
def rect(height,width):
    area = height*width
    perimeter = height*2+width*2
    return area, perimeter
    
a,p =rect(20,30)
print(f'직사각형 둘레: {p}, 면적: {a}입니다.')
```

<img src="https://dl.dropbox.com/s/o6v9c0vxpdww1lm/function-argument.png" alt="function_example" style="zoom:30%;" />



### 내장함수

내장함수 목록 확인 방법 :dir(__ __builtins____)

ex) print()

![built_in](https://user-images.githubusercontent.com/18046097/61181739-2984fd80-a665-11e9-991b-f2f058397a69.png)

#### 함수를 만들어봅시다

> 아래의 코드와 동일한 my_max 함수를 만들어주세요.
> 정수를 두개 받아서, 큰 값을 출력합니다. 
> max(1, 5)

예시 출력)
5가 더 큽니다

```python
def my_max(a,b):
#     if a> b :
#         print(f'{a}가 더 큽니다')
#         return a
#     else :
#         print(f'{b}가 더 큽니다')
#         return b
    return a if a > b else b
```

```python
# 조건표현식
def my_max(a,b,c):
    return a if a > b else b if 조건 else value ... 무한정으로 줄 수 있다.
```







### 함수의 return

앞서 설명한 것과 마찬가지로 함수는 반환되는 값이 있으며, 이는 어떠한 종류의 객체여도 상관없습니다. 
단, 오직 한 개의 객체만 반환됩니다.
함수가 return 되거나 종료되면, 함수를 호출한 곳으로 돌아갑니다.



#### 함수 정의하고 값 반환

> 리스트 두개를 받아 각각 더한 결과를 비교하여 값이 큰 리스트를 반환하는 함수를 만들어주세요.
> my_list_max([10, 3], [5, 9])

예시 출력)
[5, 9]

```
#조건 표현식
def my_list_max(list1,list2):
    return list1 if sum(list1)>sum(list2) else list2
```

```
def my_list_max(list1,list2):
    if sum(list1) > sum(list2) :
        return list1
    else :
        return list2
    
```





### 기본 인자 값 (Default Argument Values)

함수가 호출될 때, 인자를 지정하지 않아도 기본 값을 설정할 수 있습니다. 

활용법
def func(p1=v1):
    return p1

> 기본 값 활용 예제
> 이름을 받아서 다음과 같이 인사하는 함수 greeting을 작성하세요. 이름이 길동이면, "길동, 안녕?" 이름이 없으면 "익명, 안녕?" 으로 출력하세요.

```python
def greeting(name = '익명'):    #name의 defualt 값이 '익명'이다.
    return f'{name}, 안녕?'

#name = input('이름이 뭔가용?')
greeting('길동')
greeting()
```

* 기본 인자 값이 설정되어 있더라도 기존의 함수와 동일하게 호출 가능하다.

  <img src="https://user-images.githubusercontent.com/18046097/61181744-2a1d9400-a665-11e9-9095-6924ca11122e.png" alt="img" style="zoom:50%;" />

* 호출시 인자가 없으면 기본 인자 값이 활용된다.

<img src="https://user-images.githubusercontent.com/18046097/61181745-2a1d9400-a665-11e9-95ef-e50e463e1583.png" alt="function example 03" style="zoom:50%;" />

단, 기본 인자 이후에 기본 값이 없는 인자를 사용할 수는 없습니다. -> b이후의 인자들은 기본값이 있어야!!!!

```python
#올바른 예시1
def greeting(age, name ='sh'):
    return f'{name}의 나이는 {age}입니다.'
#올바른 예시2
def greeting(name ='sh',age=10):
    return f'{name}의 나이는 {age}입니다.'

greeting(19,'kim')


Out[29]:
'kim의 나이는 19입니다.'

```

```python
#틀린 예시
def greeting( name ='sh', age): #기본 인자 이후에 기본 값이 없는 인자(age)를 사용할 수는 없습니다.
    return f'{name}의 나이는 {age}입니다.'

greeting('kim',19)


  File "<ipython-input-30-99d52e1e2ac7>", line 2
    def greeting( name ='sh', age):
                 ^
SyntaxError: non-default argument follows default argument


```



### 키워드 인자(Keyword Arguments)

키워드 인자는 직접 변수의 이름으로 특정 인자를 전달할 수 있습니다.

```
greeting(name='승희',age='25')


Out[32]:
'승희의 나이는 25입니다.'
```

보통은 위치 위주가 기본이지만 __이렇게 직접 다 매개변수의 이름으로 인자들을 전달해준다면 틀린 예시의 greeting함수로도 사용이 가능하다.__



__단 아래와 같이 키워드 인자를 활용한 뒤에 위치 인자를 활용할 수는 없습니다.__

```python
greeting(age=24, '철수')

File "<ipython-input-31-216dd4cbaccf>", line 2
    greeting(age=24, '철수')
                    ^
SyntaxError: positional argument follows keyword argument

```



