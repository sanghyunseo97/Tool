# re module
```
import re
```
> 사용하는 이유는 regular expression을 사용하여 포괄적인 단어들을 찾기 위함이다.

## regular expression 사용법
1. 컴파일 후 매칭
> pattern = re.compile(**"패턴"**)
> x = pattern.search("I like apple!")
```
import re
pattern = re.compile("apple")
print(pattern.search("I like apple!").group())        # apple
```
2. 축약형
> 그냥 패턴 직접 입력
> x = re.search(**"패턴"**, **"문자열"**)

## Meta characters
- []
> []사이의 문자들 중 하나와 매치(or과 역할 비슷)
> 하이픈(-) 으로 연결 가능 ([0-9], [a-z])
> [^ ]으로 시작할 경우 반대 의미(해당 문자가 아니면 매치)
```
import re
test = "1ajgdlfkjg3skdlfj4"
pattern_1 = re.compile("[0-9]")
pattern_2 = re.compile("[^0-9]")
print(re.findall(pattern_1, test))    # ['1', '3', '4']
print(re.findall(pattern_2,test))     # ['a', 'j', 'g', 'd', 'l', 'f', 'k', 'j', 'g', 's', 'k', 'd', 'l', 'f', 'j']
```

- .(점)
> \n을 제외한 모든 문자와 매치
> 단, 문자클래스 안의 .([.])은 말 그대로 '.'을 의미함
> 또 한 가지 방법은 .앞에 \를 붙이면 된다. '\.'이면 '.' 그대로를 의미함
```
import re
test = "ab1abcabiabjab."
pattern_1 = re.compile("ab.")       # ['ab1', 'abc', 'abi', 'abj', 'ab.']
pattern_2 = re.compile("ab\.")      # ['ab.']
pattern_3 = re.compile("ab[.]")     # ['ab.']
print(re.findall(pattern_1, test))
print(re.findall(pattern_2, test))
print(re.findall(pattern_3, test))
```
- +, *
> (별)은 0회 이상 반복
> +는 1회 이상 반복

## findall
> re.findall(**패턴 문자열**, **찾는 대상의 문자열**, **플래그(없어도 됨)**
> 문자열 안에 패턴에 맞는 케이스를 전부 찾아서 리스트로 반환합니다.
```
import re
test = "aaaaaa"
test_2 = 'aaaaa'
result = re.findall('aaa', test)
result_2 = re.findall('aaa', test_2)
print(result)                           # ['aaa', 'aaa']
print(result_2)                         # ['aaa']
```

## split
> re.split(**패턴**, **찾고자 하는 문자열**, **최대 split수**, **플래그**)
> 문자열에서 패턴이 맞으면 이를 기점으로 리스트로 쪼개는 함수이다.
> 수를 지정하면 지정한 수 만큼 쪼개고 그 수가 도달하면 쪼개지 않습니다.
```
import re
test = "my name is 서상현"
test_list = re.split(" ", test, 1)
test_list_2 = re.split(' ',test )
print(test_list)                      # ['my', 'name is 서상현']
print(test_list_2)                    # ['my', 'name', 'is', '서상현']
```

## sub
> re.sub(**패턴**, **찾아서 교체할 문자열**, **대상 문자열**, **최대 교체 수**, **플래그**)
> sub는 문자열에 맞는 패턴을 2번째 인자로 교체합니다. 교체수 이상이 되면 교체하지 않는다.
```
import re
test = "Hello Hello Hello Python"
test_1 = re.sub("Hello", "Bye", test)         
print(test_1)                                 # Bye Bye Bye Python
test_2 = re.sub("Hello", "Bye", test, 2)
print(test_2)                                 # Bye Bye Hello Python
```

## search와 그 외 함수들
> re.search(**패턴**, **문자열**, **플래그**).함수이름()
> group : 패턴에 맞는 문자열을 추출
> start : 문자열의 어디서부터 패턴이 시작되는지 index 반환
> end   : 문자열의 어디서 패턴이 끝나는지
> span  : 문자열의 어디서부터 어디까지 패턴이 있는지 index 반환
```
import re
print(re.search('aa', 'baab').group())        # aa
print(re.search('aa', 'baab').start())        # 1
print(re.search('aa', 'baab').end())          # 3
print(re.search('aa', 'baab').span())         # (1, 3)
```

## Reference
- [Reference](https://velog.io/@dosilv/python-%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9Dregular-expression-%EC%82%AC%EC%9A%A9%EB%B2%95)
