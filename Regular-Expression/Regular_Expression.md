정규 표현식 Regular Expression

복잡한 문자열을 처리할 때 사용하는 기법

<br>

정규 표현식의 기초, 메타 문자

    ※ 메타 문자란 원래 그 문자가 가진 뜻이 아닌 특별한 용도로 사용되는 문자를 말한다.
    [Meta Characters] 
    	. ^ $ * + ? {} [] \ | ( )

정규 표현식에 사용되는 위 메타문자들은 특별한 의미를 갖게 된다.

<br>

문자 클래스 []

문자 클래스 [] 로 만들어진 정규식은 '  [ 와 ] 사이의 문자들의 매치  ' 라는 의미를 뜻한다. <br>

※ 문자 클래스를 만드는 메타 문자 [ 와 ] 사이에는 어떤 문자라도 들어갈 수 있다. <br>

	단, 메타 문자 '^' 가 사용될 경우에는 반대(not) 라는 의미를 갖는다.
	
	< 예시 >
	정규 표현식 [abc]는 [ 와 ] 사이의 a, b, c 중 한 개의 문자와 매치를 뜻 한다.
	만약, 입력값으로 apple을 받게 된다면, apple은 정규식과 일치하는 문자인 a가 있으므로 매치가 된다.



<br>

범위를 나타내는 하이픈(-)

하이픈(-)은 두 문자 사이의 범위 (From - To)를 의미한다.

    < 예시 >
    [a - c]  == [abc]
    [0 - 5]  == [012345]
    
    [a-zA-Z] : 알파벳 모두
      [0-9]  : 숫자

<br>

자주 사용하는 문자 클래스 모음

[0-9] 혹은 [a-zA-Z] 등은 무척 자주 사용하는 정규 표현식이다.<br>

이렇게 자주 사용하는 정규식들은 아래와 같이 별도의  표기법으로 나타낼 수 있다.

    * \d - 숫자와 매치(== [0-9])
    * \D - 숫자가 아닌 것과 매치(== [^0-9])
    * \s - whitespace 문자와 매치(== [공백\t\n\r\f\v])
    * \S - whitespace 문자가 아닌 것과 매치(== [^공백\t\n\r\f\v])
    * \w - 문자 + 숫자(Alpha-Numeric)와 매치(== [a-zA-Z0-9])
    * \W - 문자 + 숫자(Alpha-Numeric)가 아닌 문자와 매치(== [^a-zA-Z0-9])

<br>

Dot(.)

정규 표현식의 Dot(.) 메타 문자는 줄바꿈 문자인  \n 를 제외한 모든 문자와 매치됨을 의미한다.<br>

※ 참고 옵션 참고시 \n 문자와도 매치가 될 수 있게 할 수 있다.

    [의미]
    	a.b
    	=> a + 모든 문자 + b
    	a 와 b라는 문자 사이에 어떤 문자가 들어가도 모두 매치
    [예시]
    	* aab  : a 와 b 문자 사이에 a가 모든 문자를 의미하는 .과 매치
    	* a()b : a 와 b 문자 사이에 ()가 모든 문자를 의미하는 .과 매치
    	* abc  : a 와 b 문자 사이에 어떤 문자 하나라도 있어야 하는데 없기 때문에 매치 안된다.
    [유의]
    	* a.b 와 a[.]b는 서로 다른 의미를 갖는다
    		- a.b   : a 와 b 문자 사이에 모든 문자
    		- a[.]b : a 와 b 문자 사이에 .만 매치

<br>

반복 (*)

* 메타 문자는 *  바로 앞에 있는 문자가 0 부터 무한대 (2억개)  반복될 수 있음을 의미

    [예시]
    	- ca*t <----  ct  매치! : a가 0번 반복되었기에 매치 가능
    	- ca*t <----  cat 매치! : a가 1번 반복되었기에 매치 가능

<br>

반복(+)

+ 문자는 반복을 나타내는 또 다른 메타문자로서, 최소 1번 이상 반복될 때 사용된다.

    [예시]
    	- ca+t <----  ct 노매치 : a가 0번 반복되었기에 매치 불가
    	- ca+t <----  cat  매치 : a가 1번 반복되었기에 매치 가능

<br>

### 참고 문헌

**점프 투 파이썬, 저자 김응용 선생님**