# Python 변수와 문자열

## 변수

- 파이썬에서는 등호 ( = ) 를 이용해 변수에 자료를 넣는다 ( 할당한다 )

즉 ‘변수명 = data’ 같은 형태로 사용 합니다

만약 자료가 숫자라면 data에 숫자를 쓰면 되고 문자열이라면 문자열을 쓰면 된다

```python
In: abc = 12340
		print(abc)

Out:12340
```

변수에 자료를 할당한 경우 prin로 변수명에 할당한 값을 출력

또한 print 를 쓰지 않더라도 변수명을 실행해 변수에 할당된 값을 출력 할 수도 있다

```python
In : abc

Out : 12340
```

이제 값 ( 12340 ) 을 할당한 변수 abc를 이용해 앞에서 했던 계산을 그대로 해보겠습니다

```python
In:

print(abc * 1/2)
print(abc * 1/4)
print(abc * 1/5)

Out:

6170.0
3085.0
2468.0
```

앞에서 숫자 12340을 쓰는 대신 변수 abc를 이용해 연산하고 출력했다

일일이 숫자를 입력하지 않아도 되니 편하다

! 변수명을 만들 때는 아무렇게나 만들면 안 된다

  다음과 같은 규칙을 지키면서 변수명을 만들어야 한다

- **변수명은 문자,숫자,밑줄 기호(_)를 이용해 만든다**
    
    EX)   a , book1 , my_student2 , MyDog_ 등은 변수명으로 사용가능
    
    _ 는 변수명에 사용할 수 있지만 _로 시작하는 변수명은 특별한 용도에 사용하므로 보통 변수명은 _로 시작하지 않는다
    
- **숫자로 시작하는 변수명을 만들 수 없다**
    
    EX) 3star 같은 변수명은 만들 수 없다
    
- **대소문자를 구분한다**
    
    변수명 Money와 변수명 money는 서로 다른 변수다
    
    의미는 같지만 변수명은 대소문자를 구분하므로 다른 변수입니다
    
- 공백을 포함할 수 없습니다
    
    ‘my student’는 my와 student 사이에 공백이 있으므로 변수명으로 사용할 수 없습니다
    
    쓰고 싶다면 my_student와 같이 밑줄을 이용하거나 myStudent 처럼 대문자를 이용해 의미 있고 알아보기 쉬운 변수명을 사용하길 권장한다
    
- 밑줄 이외의 기호는 변수에 이용할 수 없다
    
    mystdent% , my#student , my&student 등은 변수명이 될 수 없다
    
- 다음과 같은 예약어 ( Reserved word ) 는 변수명으로 이용 할 수 없다
    
    None , True , False , and , as , assert , break , class , continue , def , del , elif ,else , except , finally , for , from , global , if , import , in , is , lambda , nonlocal , not , or , pass , raise , return , try , while , with , yield
    
    예약어인 lambda를 변수명으로 사용하기 위해 ‘lambda = 1’ 과 같이 입력하면 에러가 발생한다
    
    ### 상수
    
    프로그래밍 언어에서 어떤 숫자를 변수에 할당한 후에 프로그램이 끝날 때까지 그 변수의 값을 변경하지 않고 사용하는 경우가 있다
    
    예를들어 원주율 (파이) 인 ‘ 3.141592… ‘ 와 같이 긴 숫자는
    
    PI = 3.141592 처럼 한 번 변수에 할당한 후 계산에 필요할 때마다 PI를 사용한다
    
    이렇게 한 번 지정한 후 그 값이 변하지 않는 변수를 상수(constant variable) 라고 합니다
    

## 문자열

문자열은 문자의 나열을 의미하는데 파이썬에서는 따옴표로 둘러싸인 문자의 집합이다

### 문자열 만들기

- 문자열을 표시하기 위해 시작과 끝에 큰따옴표( “ ) 나 작은따옴표 ( ‘ ) 를 지정한다
- 둘 중 어떤것을 사용해도 되지만 양쪽에는 같은 기호를 써야 한다
- EX) “Hello world”   ‘Hello world’

```python
In:

print("String Test")

Out:

String Test
```

```python
In:

string1 = "String Test 1"
string2 = 'String Test 2'

print(string1)
print(string2)

Out:

String Test 1
String Test 2
```

이렇게 변수에 할당한 문자열의 타입( type )은 무엇일까

```python
In:

type(string1)

Out:

str
```

출력 결과는 str 입니다

문자열 안에 따옴표를 포함하려면 어떻게 할까

```python
In:

string3 = 'This is a "double" quotation test'
string4 = "This is a 'single' quotation test"

print(string3)
print(string4)

Out:

This is a "double" quotation test
This is a 'double' quotation test
```

만약 문자열에 큰따옴표와 작은따옴표 모두 포함하고 싶거나 문장을 여러 행 넣고 싶거나

입력한 그대로 출력하고 싶을 때는 문자열 전체를 삼중 ( “”” ) ( ‘’’ ) 따옴표로 감싸면 된다

```python
In:

long_string1 = '''[삼중 작은따옴표를 사용한 예]
							파이썬에는 삼중 따옴표로 여러 행의 문자열을 입력할 수 있다
							큰따옴표 ( " ) 와 작은따옴표 ( ' ) 도 입력 할 수 있다 '''

long_string2 = """ [삼중 큰따옴표를 사용한 예]
							파이썬에는 삼중 따옴표로 여러 행의 문자열을 입력할 수 있다
							큰따옴표 ( " ) 와 작은따옴표 ( ' ) 도 입력 할 수 있다 """

print(long_string1)
print(long_string2)

Out:

[삼중 작은따옴표를 사용한 예]
							파이썬에는 삼중 따옴표로 여러 행의 문자열을 입력할 수 있다
							큰따옴표 ( " ) 와 작은따옴표 ( ' ) 도 입력 할 수 있다
[삼중 큰따옴표를 사용한 예]
							파이썬에는 삼중 따옴표로 여러 행의 문자열을 입력할 수 있다
							큰따옴표 ( " ) 와 작은따옴표 ( ' ) 도 입력 할 수 있다 
```

파이썬 3.x 에서는 한글도 문자열에 이용할 수 있다

이것은 파이썬 3.x 이 유니코드( Unicode ) 를 지원해 기본적으로 문자열이 유니코드로 처리되기 때문이다

- 유니코드
    
    컴퓨터에서 문자를 표시하기 위해서는 각 문자를 컴퓨터가 이해할 수 있는 부호로 1 : 1 대응시킨 문자 코드가 필요하다
    
    대표적인 문자 코드로는 아스키코드 ( ASCII Code ) 가 있는데 이는 미국에서 제정한 것으로 영문 알파벳 , 숫자 , 몇몇 특수기호를 표시 할 수 있다
    
    컴퓨터가 전 세계적으로 쓰이면서 영어 외 다른 언어도 입력하고 표시해야 할 필요성이 생기면서 나라별로 혹은 컴퓨터 회사별로 각 나라의 언어에 맞는 문자 코드를 만들어서 사용했다
    
    **하지만 다른 문자 코드끼리 호환되지 않는 문제가 발생해 해결하기 위해 전 세계의 모든 문자를 포함하게 만든것이 바로 유니코드( Unicode ) 입니다**
    
    즉 유니코드는 컴퓨터에서 전 세계의 모든 문자를 표시 , 저장 , 처리하기 위해 만든 표준 문자코드이다
    

### 문자열 다루기

문자열에는 더하기 연산자 ( + ) 와 곱하기 연산자 ( * ) 를 이용할 수 있다

더하기 연산자 ( + ) 는 문자열끼리 연결해 문자열을 하나로 만들고

곱하기 연산자 ( * ) 는 곱한 만큼 문자열을 반복한다

```python
In:

a = 'Enjoy'
b = 'python!'
c = a + b

print(c)

Out:

Enjoy python!
```

```python
In:

print(a*3)

Out:

Enjoy Enjoy Enjoy
```

이처럼 문자열을 합치고 반복하는 것 외 문자열을 처리하는 다양한 방법이 있다