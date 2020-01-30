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
단, __오직 한 개의 객체만 반환__됩니다.
함수가 return 되거나 종료되면, 함수를 호출한 곳으로 돌아갑니다.

__함수에 return값 없으면 None이 return됨__

__반환될 때  값은 튜플 형태로 감싸져서 반환됨__



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





### 기본 인자 값 (Default Argument Values) -함수에 값 지정 안해도 될때

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

* 단, 기본 인자 이후에 기본 값이 없는 인자를 사용할 수는 없습니다. -> b이후의 인자들은 기본값이 있어야!!!!

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

#### 키워드 인자와 기본인자의 차이점 : 

#### 키워드 인자 : 함수를 호출할 때 ''매개변수 = 값'' 쓴다 vs 기본인자 : 함수를 정의(선언)할 때 ''매개변수 = 값''미리 기본값 설정 가능(중요)

--> Tip : 너무 ''키워드''인자라는 이름에 집착하지 말고 사용을 통해 느낌 익히기.

키워드 인자로만 들어갈 때는 순서가 중요 X

#### 키워드인자와 위치인자가 같이 호출 될 때 문제가 생김!!!!!!!!!!!!!!!(중요)

___요약 : 위치 인자 + 키워드 인자 (O) __
			__키워드 인자 + 위치 인자 (X)__



* 키워드 인자는 직접 변수의 이름으로 특정 인자를 전달할 수 있습니다.

```
greeting(name='승희',age='25')


Out[32]:
'승희의 나이는 25입니다.'
```

* 보통은 위치 위주가 기본이지만 __이렇게 직접 다 매개변수의 이름으로 인자들을 전달해준다면 틀린 예시의 greeting함수로도 사용이 가능하다.__



* 단 아래와 같이 키워드 인자를 활용한 뒤에 위치 인자를 활용할 수는 없습니다.
* __키워드 인자 + 위치 인자 (X)__
* __위치 인자 + 키워드 인자 (O) __

```python
greeting(age=24, '철수')

File "<ipython-input-31-216dd4cbaccf>", line 2
    greeting(age=24, '철수')
                    ^
SyntaxError: positional argument follows keyword argument

```



***

## 중요

#### 1. 키워드 인자와 기본인자의 차이점 : 

#### 키워드 인자 : 함수를 호출할 때 ''매개변수 = 값'' 쓴다 vs 기본인자 : 함수를 정의(선언)할 때 ''매개변수 = 값''미리 기본값 설정 가능(중요)

#### 2. 키워드인자와 위치인자가 같이 호출 될 때 문제가 생김!!!!!!!!!!!!!!!(중요)

___요약 : 위치 인자 + 키워드 인자 (O) __
			__키워드 인자 + 위치 인자 (X)__



***

# Python_chap3_02

20.10.23

***



__Tip 최대 재귀 횟수 보기__

```
import sys
print(sys.getrecursionlimit())
```

***

```
print('abcdf', end='\t')
원래 기본값 end가 \n인데 다른 인자를 넣어주면 그 명령에 맞게 실행한다.
```

* 보통 위치 인자(그냥 함수 매개변수의 인자를 아무것도 선언안하면 자동으로 위치별로 인식)
* 그래서 키워드 인자와 위치 인자를 둘 다 쓸꺼면 키워드인자는 무조건 맨 뒤에 와야한다.
* age, name 둘 다 키워드 인자로 넣던지, 하나만 키워드 인자로 할 꺼면 맨 뒤에 넣던지.
* 키워드 인자를 활용한 뒤에 위치 인자를 활용할 수는 없습니다.

```
def greeting(age, name ='sh'):
    return f'{name}의 나이는 {age}입니다.'

greeting(19,'kim')
```

```
#age에 철수가 들어왔다가 다시 24가 들어오니까 multiple values가 된다.
greeting( '철수',age=24)

TypeError                                 Traceback (most recent call last)
<ipython-input-4-2749f7952b06> in <module>
      1 #age에 철수가 들어왔다가
----> 2 greeting( '철수',age=24)

TypeError: greeting() got multiple values for argument 'age'
```



![image-20200123093219766](C:\Users\multicampus\Desktop\승히\Python 필기\image-20200123093219766.png)

***

유동적으로 매개변수가 변할 때

### 가변 인자 리스트 (Arbitrary Argument Lists) - (tuple튜플형태)

앞서 설명한 print()처럼 __개수가 정해지지 않은 임의의 인자를 받기 위해서__는 가변인자를 활용합니다. 
가변인자는 tuple 형태로 처리가 되며, __매개변수에 `*`로 표현__합니다. 

> 활용법
> def func(a, b, __*args__):
> *args : 임의의 개수의 위치인자를 받음을 의미
> 보통, 이 가변인자 리스트는 형식 인자 목록의 마지막에 옵니다.

__가변 리스트는 튜플 형태! - 함수 호출할 때__

```python
def my_func(*args):
    return args
print(my_func(1,2,3,4,5))
print(type(my_func()))



(1, 2, 3, 4, 5)
<class 'tuple'>
```

* 임의의 인자가 들어올 때 마다 튜플에 추가 --> 임의의 인자 개수의 __위치 인자__를 사용

* 우리가 주로 활용하는 print() 함수는 파이썬 표준 라이브러리의 내장함수 중 하나이며, 다음과 같이 구성되어있습니다.

ex) 밑 사진에서는 *objects 같은 것.



![print](https://user-images.githubusercontent.com/18046097/61181751-2b4ec100-a665-11e9-9a7c-a19a8c445cfa.png)



__가변 인자 리스트를 사용해봅시다.__

> 정수를 여러 개 받아서 가장 큰 값을 반환(return)하는 함수 my_max()를 작성하세요.
> my_max(10, 20, 30, 50)

예시출력)
50

```
def my_max(*args):
    #받아온 값 중에서 가장 큰 값을 찾아내는 logic이 필요
    #1.args가 튜플로 여러 인자들이 들어올 것이다. 하나씩 뽑을 필요가 있다.->for문
        #1-1. 첫번째 오는 값을 비교 대상으로 넣자.-> enumerate사용(for문으로 enumerate사용)
    max = 0
    for i, v in enumerate(args, start=1):
        if i == 1 :
            max = v
        #1-2. 첫번째 값이 아니면 비교 대상과 비교해서 큰 값을 비교대상에 넣는다.
        else :
            if v > max :
                max = v
    #2.for문이 끝나면 비교대상에 있는 값을 리턴한다.
    return max 
            
```



### 정의되지 않은 키워드 인자들 처리하기 (dict형태)

(키워드 인자의 값이 유동적인 숫자로(가늠불가, 정해지지 않아서) 들어올 때 -> 함수를 선언할 때 매개변수 이름 앞에 별이 두개)

정의되지 않은 키워드 인자들은 `dict` 형태로 처리가 되며, `**`로 표현합니다. 
주로` kwagrs`라는 이름을 사용하며, `**kwargs`를 통해 인자를 받아 처리할 수 있습니다.

> 활용법
> def func(**kwargs):
> 
> **kwargs : 임의의 개수의 키워드 인자를 받음을 의미

우리가 dictionary를 만들 때 사용할 수 있는 dict() 함수는 파이썬 표준 라이브러리의 내장함수 중 하나이며, 다음과 같이 구성되어 있습니다.

<img src="https://user-images.githubusercontent.com/18046097/61181740-2984fd80-a665-11e9-94cf-7f5ab41873b1.png" alt="dictionary" style="zoom: 80%;" />



* 딕셔너리 생성 함수 예시(키워드 인자)

```
dict_a = dict(한국어 = '안녕', 영어 = 'hi')
print(dict_a)

!!!!!!!
dict(1=1, 2=2) 이런식으로 생성 못함. 1,2가 식별자(등호 왼쪽)로 쓰이기 때문에, 그리고 숫자로 식별자 정할 수 없다.
```

```
#위의 경우 이렇게 사용해야 한다.
dict([(1,1),(2,2)])
or
dict(((1,1),(2,2)))


Out[33]:
{1: 1, 2: 2}
```

__정의되지 않은 키워드 인자를 처리해봅시다.__

> my_dict() 함수를 만들어 실제로 dictionary 모습처럼 출력 함수를 작성하세요.

예시 출력)
한국어: 안녕, 영어: hi, 독일어: Guten Tag

```python
#str 이용
def my_dict(**kwargs):
    result=''
    for key, value in kwargs.items():
        result += f'{key}: {value}, '
    print(result[:len(result)-2])
    
print(my_dict(한국어='안녕', 영어='hi', 독일어='Guten Tag'))

output
한국어: 안녕, 영어: hi, 독일어: Guten Tag
```

```python
#list &  join 이용
def my_dict2(**kwargs):
    res=[]
    for key, value in kwargs.items():
        res.append (f'{key}: {value}')
    return ', '.join(res)

print(my_dict2(한국어='안녕', 영어='hi', 독일어='Guten Tag'))

output
한국어: 안녕, 영어: hi, 독일어: Guten Tag
```



* 사실은 dict()는 출력이 아니라 딕셔너리를 return 합니다. 
* 딕셔너리를 return 하는 my_fake_dict() 를 작성하세요.

```python
def my_fake_dict(**kwargs):
    return kwargs

res = my_fake_dict(사과 = 'apple', 바나나 = 'banana')
print(res)

output
{'사과': 'apple', '바나나': 'banana'}
```



### 인자 리스트 언패킹 (unpacking arguments list)

* 패킹(packing) : 여러 개의 값을 하나의 컬렉션으로 묶어 변수에 대입하는 것
  collection = 1, 2, 3
* 언패킹(unpacking) : 컬렉션 속의 요소들을 여러 개의 변수에 나누어 대입하는 것
  a, b, c = collection

```python
#
list(range(3,6))

#
arg = [3, 6]
list(range(*arg))

#
```



```python
# 다음과 같이 사용할 수도 있습니다.
# =====
def save_rk(*args, **kwargs):
    return args, kwargs

res = save_rk('alice','tom','ming',forth = 'wilson', fifth = 'roy')
print(res)

output
(('alice', 'tom', 'ming'), {'forth': 'wilson', 'fifth': 'roy'})
```

```
#함수 호출할 때 언패킹해서
name = ['a','b','c']
other = {'four' : 'wilson', 'five' : 'roy'}
res1 = save_rk(*name, **other)
res2 = save_rk(name, other)
res3 = save_rk(name, **other)
res4 = save_rk(*name, other)
print(res1)
print(res2)
print(res3)
print(res4)
output
(('a', 'b', 'c'), {'four': 'wilson', 'five': 'roy'})
((['a', 'b', 'c'], {'four': 'wilson', 'five': 'roy'}), {})
((['a', 'b', 'c'],), {'four': 'wilson', 'five': 'roy'})
(('a', 'b', 'c', {'four': 'wilson', 'five': 'roy'}), {})
```







***

함수 호출 시 매개변수로 정의해서 쓸 때

가변리스트를 사용할 때 *

딕셔너리 형식으로 사용할 때 **

인자로 쓸 때 -패킹/언패킹

*만 사용

*쓰면 타입 없어지고 내용만 나온다.

* list 를 *로 언패킹하면 리스트 안에 숫자만 나온다.

```
numbers = [1,2,3,4,5]
a,b, *rest = numbers
#별을 붙이면 언패킹되서 위치 인자로 각 인자가 들어감
print(a,b)
print(rest)
print(*rest)

1 2
[3, 4, 5]
3 4 5
```

* dict를 *로 언패킹하면

```
fruits = {'바나나':2, '사과':5}
rest= fruits.items()
print(*rest)



('바나나', 2) ('사과', 5)
```



__로그인 검증 예제__

> 로그인 로직을 검증하는 함수 login 을 작성하세요.
> login 함수는 username, password, password_confirmation을 인자로 받는다.
> login 함수는 username과, password가 있는지 확인한다.
> password가 8자리 이상인지 확인한다.
> password와 password_confirmation이 일치하는지 확인한다.

```python
my_account = {
    'username': '홍길동',
    'password': '1q2w3e4r',
    'password_confirmation': '1q2w3e4r'
}
```

```python
# sign in 함수를 작성하세요.
def signin(username, password, password_confirmation):
    if len(password) < 8 :
        return '8자리 이상으로 입력해주세요.'
    else :
        if password == password_confirmation :
            return f'{username}님 회원가입이 완료되었습니다.'
        else :
            return '비밀번호가 일치하지 않습니다.'
# login 함수에 my_account를 넘겨 확인하세요.
signin(**my_account)

output :
'홍길동님 회원가입이 완료되었습니다.'
```



__[실습] URL 편하게 만들기__

> url 패턴을 만들어 문자열을 반환하는 my_url 함수를 작성하세요.
> 영진위에서 제공하는 일별 박스오피스 API 서비스는 다음과 같은 방식으로 요청을 받습니다.
> 함수는 아래에서 제공되는 기본 요청 URL에 전달되는 키워드 인자들을 key=value 의 형태로 붙여서 반환한다.
> keyword 인자가 2개 이상일 경우 & 문자로 keyword 인자들을 구분한다.
> 기본 요청 URL : http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?
> key : 발급받은 키 값(abc)
> targetDt : yyyymmdd
> itemPerPage : 1 ~ 10 **기본 10**

예시)

my_url(key='abc', targetDt='yyyymmdd')



api = {
    'key': 'abc',
    'targetDt': 'yyyymmdd'
}
my_url(**api)



예시 출력)

'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?itemPerPage=10&key=abc&targetDt=yyyymmdd&'

```python
1. 기본

api = {
    'key': '430156241533f1d058c603178cc3ca0e',
    'targetDt': '20200122'
}

def my_url(key,targetDt,itemPerPage = 10):
    #itemPerPage = 10 키워드인자를 사용하기 때문에 매개변수 중 맨 뒤에 위치
    url = 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'
    #get방식이기 때문에 위치는 상관없다
    return f'{url}itemPerPage={itemPerPage}&key={key}&targetDt={targetDt}'   
#만약 여기서 그냥 api로 인자를 넣으면 위치기반으로 key값으로 들어갈 것이다.
my_url(**api)

output:
'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?itemPerPage=10&key=430156241533f1d058c603178cc3ca0e&targetDt=20200122'


1-1. itemPerPage 빼고
def my_url(key,targetDt):
   	 url = 	'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'
    
    return f'{url}key={key}&targetDt={targetDt}'   

my_url(**api)

```

```python
2. my_url(key='abc', targetDt='yyyymmdd') 할 수 있게 제한사항 해결

def my_url(**kwargs):
    url = 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'
    for key, value in kwargs.items():
        url+=f'{key}={value}&'
        return url[:-1]
    
my_url(key='abc', targetDt='yyyymmdd')
```

```
3.기본 인자 값 추가 (itemPerPage)

def my_url(itemPerPage=10, **kwargs):
    url = 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'
    url+= f'itemPerPage={itemPerPage}&'
    for key,value in kwargs.items():
        url += f'{key}={value}&'
    
    return url[:-1]

my_url(key='abc', targetDt='yyyymmdd')
```



__실습] URL 검증하기__

> 이제 우리는 만들어진 요청 보내기전에 URL을 검증해야합니다. 
> 앞선 설명을 참고하여 검증 로직을 구현하고 문자열을 반환하세요.
> 아래의 두가지 상황만 만들도록 하겠습니다.
> key 또는 targetDt 가 없으면, 필수 요청변수가 누락되었습니다. 를 출력
> itemPerPage 의 범위가 1~10 을 넘어가면, 1~10 까지의 값을 넣어주세요. 를 출력

예시) my_url(11, **api)

출력 ) '1~10 까지의 값을 넣어주세요.'

```python
def my_url(itemPerPage=10, **kwargs):
    url = 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'
    
    #검증 추가
    if 'key' not in kwargs or 'targetDt' not in kwargs :
        return '필수 요청변수가 누락되었습니다.'
    
    if int(itemPerPage) not in range(1,11) : #정수로 입력받지만, range는 정수 비교라 int()
        return '1~10 까지의 값을 넣어주세요.'

    url+= f'itemPerPage={itemPerPage}&'
    
    for key,value in kwargs.items():
        url += f'{key}={value}&'
    
    return url[:-1]

my_url(10,**api)


    
Out[117]:
'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?itemPerPage=10&key=430156241533f1d058c603178cc3ca0e&targetDt=20200122'
```



### 이름공간(namespace)

파이썬에서 사용되는 이름들은 이름공간(namespce)에 저장되어 있습니다.
그리고,` LEGB Rule` 을 가지고 있습니다. 
변수에서 값을 찾을 때 아래와 같은 순서대로 이름을 찾아나갑니다.

* `L`ocal scope: 정의된 함수
* `E`nclosed scope: 상위 함수  (함수 안에 함수가 있는 경우)
* `G`lobal scope: 함수 밖의 변수 혹은 import된 모듈
* `B`uilt-in scope: 파이썬안에 내장되어 있는 함수 또는 속성(내장)

-->작은 범위에서 넓은 범위로 값을 찾아나감

```python
str = 4 # str을 변수로 정해버림
str(5) #내장함수 str을 쓰려면 나중에 이미 변수로 정해버린 str을 del str해줘야 scope에서 지워짐-> 나중에 변수로 쓸 수 있다.

#str은 변수인데 함수로 호출하려니까 4번 not callable
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-118-6e00f45a5b9a> in <module>
      1 #
      2 str = 4
----> 3 str(5)

TypeError: 'int' object is not callable
```

1. str() 코드가 실행되면
2. 함수에서 실행된 코드가 아니기 때문에 L, E 를 스킵하고,
3. str 을 Global scope에서 찾아서 str = 4를 가져오고, 
4. 이는 함수가 아니라 변수이기 때문에 not callable하다라는 오류를 내뱉게 됩니다.
5. 우리가 원하는 str()은 Built-in scope에 있기 때문입니다.



#### 전역변수와 지역변수의 예(전역변수 변경 x예)

```python
global_num = 5
def localscope2():
    global_num = 3 #이름만 같지 전역변수 globa_num과는 다르다
    return f'global_num 이 {global_num}으로 설정되었습니다.'

print(localscope2())
print(global_num)

output:
global_num 이 3으로 설정되었습니다.
5
```



#### 전역변수 선언 global ->전역변수 변경

```python
global_num = 5

def localscope3():
    global global_num  #선언 먼저 해야 값을 넣을 수 있다.
    global_num = 3 
    return f'global_num 이 {global_num}으로 설정되었습니다.'

print(localscope3())
print(global_num)

output:
global_num 이 3으로 설정되었습니다.
3
```

이름공간은 각자의 `수명주기`가 있습니다.

* built-in names: 파이썬이 실행된 이후부터 __영원히__ 유지
* global namespace : 모듈이 호출된 시점 이후 혹은 이름 선언된 이후부터 __인터프리터가 끝날때__ 까지 유지
* local namespace : 함수가 호출될 때 생성되고, __함수가 가 종료될 때__까지 유지 (함수 내에서 처리되지 않는 예외를 일으킬 때 삭제됨 = 에러나면 삭제)



### 재귀 함수(recursive function)

재귀 함수는 함수 내부에서 자기 자신을 호출 하는 함수를 뜻합니다.
일반적인 상황보다는 알고리즘을 구현할 때 유용하게 사용합니다.

__줄여가면서 한 점으로 수렴하게 해야 무한루프가 되지 않는다.__

#### 재귀함수 과정 보고싶으면 Python Tutor 사이트 들어가보면 된다.

__팩토리얼 계산__

> 팩토리얼은 1부터 n 까지 양의 정수를 차례대로 곱한 값이며 ! 기호로 표기합니다. 예를 들어 3!은 3 * 2 * 1이며 결과는 6 입니다.
> 팩토리얼(factorial)을 계산하는 함수 fact(n)를 작성하세요. 
> n은 1보다 큰 정수라고 가정하고, 팩토리얼을 계산한 값을 반환합니다.

예시 출력)
120

```python
1. 반복문 이용
def fact(num):
    res = 1
    while num > 1 :
        res *= num
        num -= 1
    return res

2. 재귀함수 이용
dec factorial(num):
	if num == 1 :
		return 1
	return num*factorial(num-1)


Out[134]:
120
```

<img src="https://user-images.githubusercontent.com/52446416/61354150-7b6b9480-a8ac-11e9-9172-81a33e092e85.png" alt="팩톨팩톨" style="zoom: 30%;" />



### 반복문과 재귀함수

factorial(3)
3 * factorail(2)
3 * 2 * factorial(1)
3 * 2 * 1
3 * 2
6

__두 코드 모두 원리는 같다! __

1. 반복문 코드

  * n이 1보다 큰 경우 반복문을 돌며, n은 1씩 감소한다. 
  * 마지막에 n이 1이면 더 이상 반복문을 돌지 않는다.
  * 단점 : 읽기 어렵다. 코드가 복잡
  * 장점 : 시간이 빠르다.

  

2. 재귀 함수 코드

  * 재귀 함수를 호출하며, n은 1씩 감소한다. 
  * 마지막에 n이 1이면 더 이상 추가 함수를 호출하지 않는다.
  * 단점 : 반복횟수가 크면 클수록 ->메모리 많이 잡아서 ->시간이 엄청 느려짐.
  * 장점 : 코드가 간단하다-> 오류낼 확률도 적다



> 재귀함수는 기본적으로 같은 문제이지만 점점 범위가 줄어드는 문제를 풀게 된다.
> 재귀함수를 작성시에는 반드시, `base case`가 존재 하여야 한다. 
> base case는 점점 범위가 줄어들어 반복되지 않는 최종적으로 도달하는 곳이다. 
> 재귀를 이용한 팩토리얼 계산에서의 `base case`는 n이 1일때, 함수가 아닌 정수 반환하는 것이다.

> 자기 자신을 호출하는 재귀함수는 알고리즘 구현시 많이 사용된다.
> 코드가 더 직관적이고 이해하기 쉬운 경우가 있다. (하지만, 만들기는 어려움)
> Python Tutor에 보면, 함수가 호출될 때마다 메모리 공간에 쌓이는 것을 볼 수 있다.
> 이 경우, 메모리 스택이 넘치거나(Stack overflow) 프로그램 실행 속도가 늘어지는 단점이 생긴다.
> 파이썬에서는 이를 방지하기 위해 1,000번이 넘어가게 되면 더이상 함수를 호출하지 않고, 종료된다. (최대 재귀 깊이)



__파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 3,000으로 정해져 있기 때문입니다.__



__최대 재귀 횟수 보기__

```
import sys
print(sys.getrecursionlimit())
```



### 반복문과 재귀 함수의 차이

알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수를 사용한다.
재귀 호출은 변수 사용 을 줄여줄 수 있다.



### 피보나치 수열

> 첫째 및 둘째 항이 1이며 그 뒤의 모든 항은 바로 앞 두 항의 합인 수열입니다. 
> (0), 1, 1, 2, 3, 5, 8
> 피보나치 수열은 다음과 같은 점화식이 있습니다. 
> 피보나치 값을 리턴하는 두가지 방식의 코드를 모두 작성해주세요.
>
> (𝑛∈{2,3,4,…})
> Fn=Fn−1+Fn−2(n∈{2,3,4,…})
> 1) `fib(n) `: 재귀함수
> 2) `fib_loop(n)` : 반복문 활용한 함수

예시 입력)
fib(10)

예시 호출)
55

```python
1. 재귀 이용
def fib(num) :
    if num < 2 :
        return num
    else :
        return fib(num-1) + fib(num-2)
fib(10)


Out[140]:
55
```

```python
2. 반복문 이용(list이용)
def fib_loop(num):
    if num < 2 :
        return num
    res = [0, 1]
    for i in range(2, num+1):
        res.append(res[i-1]+res[i-2])
    return res[-1]
   
fib_loop(10)


Out[144]:
55
```

```python
2-2. 반복문 이용(list이용 x)
def fib_loop_2(num):
    if num < 2 :
        return num
    a,b = 0 ,1
    
    for i in range(2,num+1):
        a, b = b, a+b  # 이전 값과 그 이전 값
    
    return b

fib_loop_2(10)


Out[149]:
55
```

***



## 중요

### 1. 가변 인자 리스트 (Arbitrary Argument Lists) - (tuple튜플형태)

__개수가 정해지지 않은 임의의 인자를 받기 위해서__는 가변인자를 활용

* 가변인자는 tuple 형태로 처리가 되며, __매개변수에 `*`로 표현__

> 활용법
> def func(a, b, __*args__):
> *args : 임의의 개수의 위치인자를 받음을 의미
> 보통, 이 가변인자 리스트는 형식 인자 목록의 마지막에 옵니다.

* 임의의 인자가 들어올 때 마다 튜플에 추가 --> 임의의 인자 개수의 __위치 인자__를 사용



### 2. 정의되지 않은 키워드 인자들 처리하기 (dict형태로 만들어줌)

(키워드 인자의 값이 유동적인 숫자로(가늠불가, 정해지지 않아서) 들어올 때 -> 함수를 선언할 때 매개변수 이름 앞에 별이 두개)

정의되지 않은 키워드 인자들은 `dict` 형태로 처리가 되며, `**`로 표현합니다. 
주로` kwagrs`라는 이름을 사용하며, `**kwargs`를 통해 인자를 받아 처리할 수 있습니다.

> 활용법
> def func(**kwargs):
> 
> **kwargs : 임의의 개수의 키워드 인자를 받음을 의미

ex) dict_a = dict(한국어 = '안녕', 영어 = 'hi') -> 키워드 인자(A = 'b') 2개인 것을 알 수 있다.



### 3. 가변인자리스트와 정의되지 않은 키워드 인자들 처리 차이점 

#### 가변인자리스트 : 여러개의 위치 인자를 받아옴, 별 1개 *(tuple) 

#### 정의되지 않은 키워드 인자들 처리 : 여러개의 키워드 인자를 받아옴, 별 2개 **(dict)



### 4. 인자 리스트 언패킹

: 포장지로 감싸진 리스트나 튜플의 포장지를 벗겨서 인자를 하나씩 줘서 처리할 수 있다.



### 5. *의 사용 2가지 -가변인자리스트와 인자 리스트 언패킹의 차이점

#### 함수 정의할 때 별* 붙어있으면 :  가변인자리스트

#### 함수 호출할 떄 별* 붙어있으면 : 언패킹



### 6. 이름공간(namespace)

파이썬에서 사용되는 이름들은 이름공간(namespce)에 저장되어 있습니다.
그리고,` LEGB Rule` 을 가지고 있습니다. 



### 7. 재귀 함수(recursive function)

단점 : 시간 많이 걸리고, 메모리도 많이 든다. - > 호출할 수록 느려지고 자칫 잘못하면 무한루프에 빠짐

장점 : 코드가 심플, 가독성이 좋다

재귀함수는 기본적으로 같은 문제이지만 점점 범위가 줄어드는 문제를 풀게 된다.
재귀함수를 작성시에는 반드시,` base case`가 존재 하여야 한다. 
base case는 점점 범위가 줄어들어 반복되지 않는 최종적으로 도달하는 곳이다. 
재귀를 이용한 팩토리얼 계산에서의 `base case`는 n이 1일때, 함수가 아닌 정수 반환하는 것이다.