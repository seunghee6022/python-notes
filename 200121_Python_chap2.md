# pPython_Chap2_1

20.01.21

__내장함수 링크__

https://docs.python.org/ko/3.6/library/functions.html

***

### 제어문

지금까지의 코드는 위에서부터 아래로 순차적으로 명령을 수행하는 프로그램을 작성하였습니다. 
제어문(Control of Flow)은 크게 반복문과 조건문으로 나눌 수 있고, 이는 순서도(Flow chart)로 표현이 가능합니다.

![if flowchart](https://user-images.githubusercontent.com/18046097/61180553-25e87b00-a653-11e9-9895-7976d7204734.png)

```python
a=5
if a>5 :
    print("5 초과")
else :
    print("5 이하")
print(a)

```



### 조건문

1. if 문은 반드시 일정한 참/거짓을 판단할 수 있는 조건식과 함께 사용이 되어야한다. if <조건식>:
   1-1. <조건식>이 참인 경우 : 이후의 문장을 수행한다.
   1-2. <조건식>이 거짓인 경우 else: 이후의 문장을 수행한다.
   1-3. 여러 개의 elif 부가 있을 수 있고(없거나), else는 선택적이다.
   * 이때 반드시 들여쓰기를 유의해야한다. 파이썬에서는 코드 블록을 자바나 C언어의 {}와 달리 들여쓰기로 판단하기 때문이다.
   * 앞으로 우리는 PEP-8에서 권장하는 4spaces를 사용할 것이다.![if style](https://user-images.githubusercontent.com/18046097/61180564-3a2c7800-a653-11e9-9fba-d60d2688ed3a.png)

![[우리는 4spaces를 맞춰서 씁니다!]](https://user-images.githubusercontent.com/18046097/61180566-3ac50e80-a653-11e9-81a6-2f195eeb0a65.png)

```python
num = int(input('숫자를 입력하세요 : '))
if num % 2  :
    print("홀수입니다") #나머지가 1이면 true이므로
else :
    print("짝수입니다.") #나머지가 0이면 false이므로
```



### 복수 조건문

2개 이상의 조건문을 활용할 경우 elif <조건식>:을 활용합니다.

![elif](https://user-images.githubusercontent.com/18046097/61180560-3993e180-a653-11e9-8263-79bd7bc6eed7.png)



>  조건문을 통해 변수 score에 따른 평점을 출력하세요.

```
score = int(input('점수를 입력하세요 : '))
if score >= 90 :
    print("A")
elif score >= 80 :
    print("B")
elif score >= 70 :
    print("C")
elif score >= 60 :
    print("D")
else :
    print("F")
```



###  중첩조건문

> 위 실습문제 2개 코드를 활용하여 95점 이상이면, "참 잘했어요"도 함께 출력해주세요.

```python
score = 96
if score >= 90 :
    print("A")
    if score >= 95:
        print("참 잘했어요.")
elif score >= 80 :
    print("B")
elif score >= 70 :
    print("C")
elif score >= 60 :
    print("D")
else :
    print("F")
```



### 조건 표현식(Conditional Expression)

표현식은 보통 조건에 따라 값을 정할 때 많이 활용됩니다.

활용법
__true_value if <조건식> else false_value__

조건식이 참이면 true_value를 거짓이면 false_value를 반환

```python
num = 2
print('0 보다 큼') if num > 0 else print('0 보다 크지않음')

0 보다 큼
```



> 조건표현식 만들어보기
> 다음의 코드와 동일한 조건 표현식을 작성해보세요.
>
> num = 2
> if num % 2:
>     result = '홀수입니다.'
> else:
>     result = '짝수입니다.'
> print(result)

예시 출력)
짝수입니다.

```python
num = 2
result='홀수입니다.' if num % 2  else '짝수입니다.' 
print(result)

짝수입니다.
```



### 반복문

#### while문

`while` 문은 조건식이 참(True)인 경우 반복적으로 코드를 실행합니다.
그래서 종료조건을 반드시 설정해주어야 합니다.

![while](https://user-images.githubusercontent.com/18046097/61180568-3ac50e80-a653-11e9-9960-ba15137290a6.png)

```python
a = 0
while a < 5:
    print(a)
    a += 1
    
print("끝")
```



![img](https://user-images.githubusercontent.com/18046097/61180567-3ac50e80-a653-11e9-9f12-39c404f4be30.png)

`while` 문 역시 `<조건식>` 이후에 `:`이 반드시 필요하며, 
이후 오는 코드 블록은` 4spaces`로 들여쓰기를 해주셔야 합니다.



>사용자가 "안녕"이라고 입력할 때까지 인사하는 코드를 작성해보세요.

```
greeting = ' '
while greeting != '안녕' :
        greeting = input("안녕! 안녕이라고 말해줘!")
```



### for문

for 문은 정해진 범위 내 시퀀스(문자열, 튜플, 리스트 같은)나 다른 반복가능한 객체(iterable)의 요소들을 순차적으로 코드를 실행합니다.

![img](https://user-images.githubusercontent.com/18046097/61180565-3a2c7800-a653-11e9-806a-28838248de31.png)

```
for a in range(5):
    print(a)
```



![for animation](https://user-images.githubusercontent.com/18046097/61180563-3a2c7800-a653-11e9-8a7a-c7d6e6b30141.gif)



for 문에서 요소 값에 다른 값을 할당해도 다음 반복구문에 영향을 주지 않습니다.
다음 range 요소 값에 의해 덮어 씌워지기 때문입니다.

```python
for i in range(5):
	print(i)
	i = 10  #영향 주지 않는다
	

0
1
2
3
4
```



#### for 문과 if 문 작성하기

#### index와 함께 for문 활용

> enumerate()를 활용하면, 추가적인 변수를 활용할 수 있습니다.
> enumerate()는 파이썬 표준 라이브러리의 내장함수 중 하나이며, 다음과 같이 구성되어 있다.

![image-20200121140142009](C:\Users\multicampus\Desktop\승히\Python_day1\image-20200121140142009.png)



```python
lunch = ['짜장면', '초밥']
for i in enumerate(lunch):
    print(i)
    


(0, '짜장면')
(1, '초밥')
```

```python
for idx,menu in enumerate(lunch):
    print(idx)
    print(menu)
    

0
짜장면
1
초밥
```

```python
classroom = ['Kim', 'Lee', 'Park']
classlist = list(enumerate(classroom))
print(classlist)
print(type(classlist[0]))

[(0, 'Kim'), (1, 'Lee'), (2, 'Park')]
<class 'tuple'>
```

```python
classlist2 = list(enumerate(classroom,start=1))
print(classlist2)
print(type(classlist2[0]))

[(1, 'Kim'), (2, 'Lee'), (3, 'Park')]
<class 'tuple'>
```



#### dictionary 반복문 활용

```python
classroom = {'teacher' : 'Kim','student1' : 'Um', 'student2 ': 'Jeong', 'student3' : 'Mun'}
for member in classroom :
    print(member)
    
teacher
student1
student2 
student3
```

dictionary의 key를 출력함으로써 value에도 접근할 수 있기 때문입니다.

```python
for member in classroom :
    print(classroom[member])

Kim
Um
Jeong
Mun
```

#### dictionary에서 'for'활용하는 4가지 방법

0. dictionary (key반복)

```
for key in dict:
	print(key)
```

1. key반복

```
for key in dict.keys():
	print(key)
```

2. value 반복

```
for value in dict.values():
	print(value)
```

3.  key, value 반복

```
for key,value in dict.items():
	print(key, value)
```



__dictionary for문 작성하기__

> 4가지 반복문을 활용해보고 출력되는 결과를 확인해보세요.
> blood_type = {'A': 4, 'B': 2, 'AB': 3, 'O':1}

예시 출력)
혈액형의 종류는 다음과 같습니다 =>  A B AB O
혈액형의 종류는 다음과 같습니다 =>  A B AB O
총인원은 10명입니다.
A형은 4명입니다. ... O형은 1명입니다.

```python
blood_type = {'A': 4, 'B': 2, 'AB': 3, 'O':1}
s = "혈액형의 종류는 다음과 같습니다 => "
cnt = 0
tot = ""
for blood in blood_type:
    s+= f' {blood}'
    cnt += blood_type[blood]
    tot += f'{blood}은 {blood_type[blood]}명입니다.'
    
print(s)
print(f'총인원은 {cnt}명입니다.')
print(tot)



혈액형의 종류는 다음과 같습니다 =>  A B AB O
총인원은 10명입니다.
A은 4명입니다.B은 2명입니다.AB은 3명입니다.O은 1명입니다.
```

```python
ss = "혈액형의 종류는 다음과 같습니다 => "
for b in blood_type.keys():
    ss += ' '+b
print(ss)



혈액형의 종류는 다음과 같습니다 =>  A B AB O
```

```python
tn = 0
for n in blood_type.values():
    tn += n
print(f"총인원은 {tn}명입니다.")



총인원은 10명입니다.
```

```python
for b,v in blood_type.items():
    print(f'{b}형은 {v}명입니다.',end = ' ')
    

A형은 4명입니다. B형은 2명입니다. AB형은 3명입니다. O형은 1명입니다. 
```



#### dictionary 구축하기 (for, if)

> 다음과 같은 리스트가 있을 때 각각의 요소의 개수를 value 값으로 갖는 딕셔너리를 만드세요.
> book_title =  ['great', 'expectations', 'the', 'adventures', 'of', 'sherlock', 'holmes', 'the', 'great', 'gasby', 'hamlet', 'adventures', 'of', 'huckleberry', 'fin']

예시 출력)
{'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}                 

* for, if 사용

 ```python
summary = {}
for book in book_title :
    if book in summary :
        summary[book] += 1
    else:
        summary[book] = 1
print(summary)    
 ```

* .count() 사용

```python
s = {}
for book in book_title :
    summary[book] = book_title.count(book)
print(summary)
```

* 3 .get() method (4장에서 다시 배웁니다.)

  > get(key[, default])
  > key 가 딕셔너리에 있는 경우 key 에 대응하는 값을 돌려주고, 그렇지 않으면 default 를 돌려준다. 

```python
summary = {}
for book in book_title:
    summary[book] = summary.get(book, 0) + 1
    #값이 있으면 해당되는 value값 넘어옴. 없을 땐 default = 0
print(summary)
```



### range() 함수

숫자들의 시퀀스로 반복 할 필요가 있으면 사용하는 함수입니다. 수열을 만듭니다.
__range(start, stop[, step])__

* step 인자가 생략되면 기본값 1이 사용된다. 
* start 인자가 생략되면 기본값 0이 사용된다. 
* step 이 0이면 ValueError를 일으킨다.

__장점__
list 나 tuple 에 비해 범위의 크기에 무관하게 항상 같은 (작은) 양의 메모리를 사용한다. (start, stop, step 값만을 저장).

__주의사항__
range() 가 돌려준 객체(iterable)는 리스트인 것 같지만, 리스트가 아니다. 
반복(이터레이트)할 때 원하는 시퀀스 항목들을 순서대로 돌려주는 객체이지만, 실제로 리스트를 만들지 않아서 공간을 절약하는 것이다.



### break, continue, else, pass

#### break

`break` 문은 반복문을 종료하는 표현입니다. 
`for` 나 `while `문으로부터 빠져나가게 만듭니다.

```python
rice = ['보리', '보리', '보리', '쌀', '보리']

for i in rice:
    if i == '쌀':
        print("잡았다!")
        break

```

> 조건문과 반복문, break를 활용하여 다음 headlines 리스트의 요소들을 130자 크기의 하나의 문자열로 이어 붙이는 코드를 작성하세요.
> headlines = [
>     "Local Bear Eaten by Man",
>     "Legislature Announces New Laws",
>     "Peasant Discovers Violence Inherent in System",
>     "Cat Rescues Fireman Stuck in Tree",
>     "Brave Knight Runs Away",
>     "Papperbok Review: Totally Triffic"
> ]

예시 출력)
Local Bear Eaten by Man Legislature Announces New Laws Peasant Discovers Violence Inherent in System Cat Rescues Fireman Stuck in

```python
title =''
for i in headlines :
    title += i+' '
    if len(title) >= 130 :
        title = title[:130]
        break
print(title) 
```



#### continue
continue문은 continue 이후의 코드를 수행하지 않고 다음 요소를 선택해 반복을 계속 수행합니다.

> 나이가 입력된 리스트가 있을때, 조건문과 반복문, continue를 활용하여 20살 이상일때만 "성인입니다"라는 출력을 하는 코드를 작성하세요.
> ages = [10, 23, 8, 30, 25, 31]

예시 출력)
23 살은 성인입니다.
30 살은 성인입니다.
25 살은 성인입니다.
31 살은 성인입니다.

```python
ages = [10, 23, 8, 30, 25, 31]
for age in ages :
    if age < 20 :
        continue
    else :
        print(f'{age} 살은 성인입니다.')
        
```



#### else

* else 문은 끝까지 반복문을 시행한 이후에 실행된다.
* 반복에서 리스트의 소진이나 (for 의 경우) 조건이 거짓이 돼서 (while 의 경우) 종료할 때 실행된다. 
* 하지만 반복문이 break 문으로 종료할 때는 실행되지 않는다. (break를 통해 중간에 종료되지 않은 경우만 실행)

```python
for i in range(10):
    if i is 100 :
        break
    print(i)
else :
    print('정상 반복 완료!')

0
1
2
3
4
5
6
7
8
9
정상 반복 완료!
```

break 이후에 else문 실행 되지 않음

```python
for i in range(10):
    if i is 5 :
        break
    print(i)
else :
    print('정상 반복 완료!')
    
0
1
2
3
4
```



> else 문 작성하기
> 조건문과 반복문, break, else 를 통해서 아래의 코드와 동일한 코드를 작성하세요.
> 3이 있을 경우 True를 print하고, 아닐 경우 False를 print 한다.
> numbers = [1, 5, 10]

예시 출력)
False

```python
numbers = [1, 5, 10]
for i in numbers :
    if i == 3:
        print("True")
        break       
else :
    print("False")
```



#### pass

pass 문은 아무것도 하지 않습니다. 문법적으로 문장이 필요하지만, 프로그램이 특별히 할 일이 없을 때 자리를 채우는 용도로 사용할 수 있습니다.

`pass` 와 `continue` 차이

1.pass  - dummy 같은 것, 아무것도 하지 않는다

```
for i in range(10):
    if i==3:
        pass
    print(i)
    


0
1
2
3
4
5
6
7
8
9
```

2. continue 

```
for i in range(10):
    if i==3 :
        continue
    print(i)
    
0
1
2
4
5
6
7
8
9
```

