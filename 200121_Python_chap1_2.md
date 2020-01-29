# Python 2일차

20.01.21

***

### 단축평가



### 복합연산자

* +=
* -=
* *=



### 기타연산자



### Containment Test

in 사용 요소 속해있는지 여부 판단

```
'p' in 'apple' 

2 in [1,2,3]

5 in range(5)
```



### Identity

```
a= 3
b= 2
a is b
```

```
id(256)
id(5)

Out[2]:
140722586419824
140722586411792
```

### Indexing

```
# 파이썬에서 -5 부터 256 까지의 같은 숫자일 때의 id는 동일합니다.
print(id(5))
print(id(5))

140722586411792
140722586411792
```

```
#257 이후의 id 는 다릅니다.
print(id(257))
print(id(257))

1841601241744
1841601241488
```



### Slicing

```
1. Indexing
'hi'[0]

h
```

```
2. Slicing
'hello'[1:3]

ell
```

### 연산자 우선순위

1. ()을 통한 grouping
2. Slicing
3. Indexing
4. 제곱연산자 **
5. 단항연산자 +, - (음수/양수 부호)
6. 산술연산자 *, /, %
7. 산술연산자 +, -
8. 비교연산자, in, is
9. not
10. and 
11. or



### 기초형변환(Type conversion, Typecasting)

![typecasting](https://user-images.githubusercontent.com/18046097/61180466-a6a67780-a651-11e9-8c0a-adb9e1ee04de.png)

파이썬에서 데이터타입은 서로 변환할 수 있습니다.



1. __암시적 형변환(Implicit Type Conversion)__

사용자가 의도하지 않았지만, 파이썬 내부적으로 자동으로 형변환 하는 경우입니다. 아래의 상황에서만 가능합니다.

* bool
* Numbers (int, float, complex)

ex) bool + integer 더할 수 있다. -> True + 3 = 4

```python
1. bool + integer => integer
True + 3 

4
```

```python
2. int + float => float
int_num = 3
float_num = 5.0
comp_num = 3+5j
int_float = int_num + float_num
print(int_float)
print(type(int_float))



8.0
<class 'float'>
```

```python
3. int + complex => complex
int_comp = int_num + comp_num
print(int_comp)
print(type(int_comp))

(6+5j)
<class 'complex'>
```



2. __명시적인 형변환(Explicit Type Conversion)__

   위의 상황을 제외하고는 모두 명시적으로 형 변환을 해주어야

   * string -> intger : 형식에 맞는 숫자만 가능
   * integer -> string : 모두 가능

   암시적 형변환이 되는 모든 경우도 명시적으로 형변환이 가능

   * int() : string, float를 int로 변환
   * float() : string, int를 float로 변환
   * str() : int, float, list, tuple, dictionary를 문자열로 변환 

   list(), tuple() 등은 다음 챕터에서 배울 예정

   

```python
a= 'hi'
int(a)
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-14-22db96bebd0a> in <module>
      1 #
      2 a= 'hi'
----> 3 int(a)

ValueError: invalid literal for int() with base 10: 'hi'
```

```python
a= '3.5'
b=float(a)
int(b)

3 #소수점없이 정수부분만 남게 됨
```



### sequence 시퀀스 자료형

시퀀스는 데이터가 __순서대로 나열된 형식__을 나타냅니다. 

__주의! 순서대로 나열된 것이 정렬되었다라는 뜻은 아니다.__

파이썬에서 기본적인 시퀀스 타입

* 리스트(list)
* 튜플(tuple)
* 레인지(range)
* 문자열(string)
* 바이너리(binary)



1. 리스트( list) - mutable

```python
# l과 ll 둘다 []로 같다.
l = list()
ll = []
location = ['서울','대전','대구','부산','구미']
```

```python
# mutable = 수정가능하다
location[0]
location[1] = '광주'
print(location)

['서울', '광주', '대구', '부산', '구미']
```

2. 튜플(tuple )  immutable

```python
# 튜플 만드는 방법 1
tuple_ex = (1,2)
print(type(tuple_ex))
# 튜플 만드는 방법 2
tuple_ex2 = 1, 2
print(tuple_ex2)
print(type(tuple_ex2))


<class 'tuple'>
(1, 2)
<class 'tuple'>
```

```
x, y =(1, 2)
print(x)
print(y)
```

```
x, y = (y, x)
print(x)
print(y)
```

```
empty = ()
print(type(empty))
print(len(empty))

<class 'tuple'>
0
```

__하나의 항목으로 구성된 튜플은 값 뒤에 쉼표를 붙여서 만듭니다. __

```python
single_tup = ('hello')
print(single_tup)
print(type(single_tup))
print(len(single_tup))

hello
<class 'str'>
5
```

```python
single_tup = ('hello',) #!!!!!!!!!!!!!!!!!!!! ,추가
print(single_tup)
print(type(single_tup))
print(len(single_tup))

('hello',)
<class 'tuple'>
1
```



3. 레인지(range)

range 는 숫자의 시퀀스를 나타내기 위해 사용됩니다.
기본형 : `range(n) `

> 0부터 n-1까지 값을 가짐 

범위 지정 : range(n, m) 

> n부터 m-1까지 값을 가짐

범위 및 스텝 지정 : range(n, m, s)

> n부터 m-1까지 +s만큼 증가한다

```
# 0부터 -9까지 담긴 range를 만들어봅시다.
l = list(range(0,-10,-1))
print(l)


[0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
```



4. 문자열(string)

__시퀀스에서 활용할 수 있는 연산자/함수__

![image-20200121104310844](C:\Users\multicampus\Desktop\승히\Python_day1\image-20200121104310844.png)

```
string = 's'
'a' in string

False
```

```
print("안녕"+"하세여")
print((1,2)+(3,4))
print([1,2]*3)

안녕하세여
(1, 2, 3, 4)
[1, 2, 1, 2, 1, 2]
```

* slicing

```python
lunch = ['김치찌개', '불고기', '치킨필라프','닭가슴살','고구마','콜라']
lunch[1:3]

['불고기', '치킨필라프']
```

```python
l=list(range(0,31,3))
print(l)
print(l[0:31:2])

[0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
[0, 6, 12, 18, 24, 30]
```

* max/min

```
sample=list(range(0,31,3))
print(max(sample))
print(min(sample))

30
0
```

* count

```
s=[1,2,1,3,1,4]
print(s.count(1))

3
```



5. set

   `set`은 순서가 없는 자료구조입니다.
   `dictionary`는 아이템이 삽입되는 순서를 가지고 있습니다.

중복된 값 x

빈 집합 만들려면 set() 사용해야!  __{} 사용 안됨!!!!!!!!!!!!!!__ 이건 딕셔너리

![image-20200121110825000](C:\Users\multicampus\Desktop\승히\Python_day1\image-20200121110825000.png)

```python
set_a={1, 2, 3}
set_b = {3, 6, 9}
print(set_a - set_b) # 차집합
print(set_a | set_b) # 합집합
print(set_a & set_b) # 교집합

{1, 2}
{1, 2, 3, 6, 9}
{3}
```

* set을 활용하면 list의 중복된 값을 손쉽게 제거할 수 있습니다.

  ```python
  list_a =[1,3,5,1,2,3,6]
  set_d = set(list_a)
  print(set_d)
  list(set_d)
  
  
  {1, 2, 3, 5, 6}
  [1, 2, 3, 5, 6]
  ```

6. dictionary 딕셔너리

* 딕셔너리는 key와 value가 쌍으로 이뤄져있으며, 궁극의 자료구조이다. 
* {}를 통해 만들며, dict()로 만들 수도 있다.
* key는 불변(immutable)한 모든 것이 가능하다. (불변값 : string, integer, float, boolean, tuple, range)
* value는 list, dictionary를 포함한 모든 것이 가능하다.

```python
dic_c ={1: 1, 2: 2, 3: 3, 1: 4}
print(dic_c)


#나중에 생성된 키의 value값으로 덮어쓰기됨
{1: 4, 2: 2, 3: 3}
```

```python
phone_book = {'서울': '02', '경기': '031', '구미': '054'}
s2 = phone_book.keys()
s3 = phone_book.values()
print(s2)
print(type(s2))


#리스트로 갖고 싶으면 형변환 해야한다.
dict_keys(['서울', '경기', '구미'])
dict_values(['02', '031', '054']) #메모리 관리를 위해 치스트 형식으로 보여주기만 하고 저장은 하지 않는다.
<class 'dict_keys'>
<class 'dict_values'>
```

```python
# 딕셔너리의 .items() 메소드를 활용하여 key, value를 확인 해볼 수 있습니다.
s4 = phone_book.items()
print(s4)
print(type(s4))

dict_items([('서울', '02'), ('경기', '031'), ('구미', '054')])
<class 'dict_items'>
```

***

### 정리

![container](https://user-images.githubusercontent.com/18046097/61180439-44e60d80-a651-11e9-9adc-e60fa57c2165.png)