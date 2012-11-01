꽃보다 Scala

꽃보다 Scala

# Before Started...

최근 Scala라는 언어에 대해서 들어본 분이 많을 것이라 생각됩니다. Scala는 Ruby On Rails 처럼 수많은 관심을 이끌어 내며
화려하게 등장하지는 않았지만,  이미 Twitter, Foursquare, Tumblr 등의 잘나간다하는 소프트웨어 회사들에서 주 언어로
쓰이며 조용히 자신의 존재감을 널리 알리고 있습니다. Scala가 많은 대형 서비스에서 쓰이고 있다는 점은, Scala가 단순히 언어적
화려함이나 문법 설탕(syntactic sugar) 덩어리가 아니라,  그 만큼 강력하며 안정성 있는 언어라는 점을 보여줍니다.

이 글의 목적은 이렇게 요즘 뜨는 Scala 라는 언어에 대한 소개와 몇몇 Scala framework들에 대한 소개를 통해 여러분의 지적
욕구를 자극하고 Scala를 널리 알려 여러분을 이롭게 하고자 하는데 있습니다.

하지만, 익히 알려진데로 함수형 언어에 익숙지 않고 하나의 언어 (특히 자바) 만을 사용했던 개발자라면 Scala 는 극악의 난이도로 다가올
수도 있습니다. Scala의 창시자인 Martin Odersky가 저자로 참여한  “Programming in Scala 2nd
Edition” 의 머리말에 보면 이런 문구가 나옵니다.

“Scala will challenge you. That’s part of the joy of using it. You won’t
understand the full power of its type system by the end of your first day. You
won’t understand the zen of objects being functions and functions being
objects in your first week. …”

한마디로, Scala는 어렵습니다. 하고자 하는 바도 많고 할 수 있는 것이 많기 때문에 그만큼 유연하고 그만큼 복잡합니다. 그런것을 배워
나가는것 또한  개발자의 큰 즐거움 아닐까 합니다 :)

# What is Scala?

Scala는 Martin Odersky 라는 독일인 컴퓨터 과학자에 의해 2001년에 시작되었으며 2003년에 첫 release가 이루어진,
JVM과 .NET 을 런타임으로 하는 프로그래밍 언어입니다. Martin Odersky는 이전에는 Java의 Generic과 Sun의
java compiler 를 위해 일했었다고 합니다.

Scala 라는 이름은 “Scalable Language” 의 약자라고 알려져 있습니다. “scalar” (수 또는 양, <->
vector) 나 “scholar” (학자, 학식이 있는 사람) 등의 단어를 떠오르는게 왠지 나중에 약자를 붙인 게 아닐까 의심이 들기도
합니다만, 이름은 중요하지 않습니다. 이 Language가 어떤 놈이고 왜 써야하고 얼마나 훌륭한 놈인지가 오늘의 주제이니까요.

* 이하 모든 내용은 JVM을 기반으로 합니다. 

## JVM 기반 언어

Scala는 Groovy나 Clojure 등의 언어처럼 JVM을 실행환경으로 하며, 컴파일러를 통해 자바 바이트 코드로 컴파일 됩니다. 즉,
“.scala” 파일을 컴파일 하면  “.class” 파일이 나오며, 이후로는 자바와 동일하게 다뤄도 무방하며, Scala는 이를 통해
아래와 같은 특징들을 가지게 됩니다.

### 1. 모든 표준 JVM 위에서 구동 가능

Scala는 컴파일되면 “.class” 파일이 되며, 구동시에는 자바에서 컴파일된 class와 차이가 없습니다. 따라서 모든 표준 JVM에서
구동가능하며, “.class” 파일이 만들어지기 때문에, Dalvik 위에서도 구동 가능합니다.

### 2. 수많은 자바 라이브러리 및 툴 사용 가능

Scala는 자바와 상호 운영성(interoperability)를 가집니다. 실행시에는 단순히 “.class” 파일 이기 때문에 아무런 문제
없이 수많은 오픈 소스 라이브러리를 자바와 마찬가지로 그대로 사용 할 수 있습니다.

### 3. 성능 손실 없음

Scala 컴파일러는 성능 손실을 발생시키지 않습니다. 동일한 목적의 코드라면 Scala를 사용했다고 해서 자바보다 성능이 떨어질 일은
없습니다. 또한, Scala가 가지는 많은 강점들은 모두 Compile time 에 이루어지며 reflection 등을 이용해 runtime
에 이루어 지지 않습니다.  앞으로 언급할 모든 강력한 Scala의 기능들은 컴파일 타임에 이루어집니다.

모든것은 컴파일 타임에!

## 객체 지향 언어 (Object-oriented language)

Scala는 객체 지향 언어입니다. 기본적으로 자바와 유사한 형태의 객체 지향을 지원하지만, Scala는 자바보다 Smalltalk에 가까운
순수한 객체 지향 언어로 자바와는 다음과 같은 점이 다릅니다.

### No primitive type

자바와 달리, Scala는 모든 정수/실수 형태의 값 들 역시 객체로 표현되며, operator overloading을 통해 해당 객체에
대한 연산을 지원합니다. 예를 들자면 1+1 의 연산은  1.+(1)  과 같으며 + 는 Int 객체에 정의된 instance method
입니다.

### Trait

Scala는 trait 이라는 형태의 container를 제공합니다. 기본적으로 자바의 Interface와 유사하지만, Scala의
trait은 메소드에 대한 구현을 가질 수 있으며 변수 역시 가질 수 있습니다. 또한, mix-in composition이라 불리는 다중
상속과 유사한 기능을 제공하며, 부모 클래스에대한 구체적인 명시 없이 코딩을 할 수 있기 때문에 좀더 “pluggable” 한 코드를 작성
가능합니다.

* Spring 이나 Guice 같은 별도의 엔진 없이도 DI가 가능합니다. (cake pattern)

## 함수형 언어 (Functional language)

Scala는 함수형 언어(functional language) 입니다. 동시에 객체 지향 언어이기 때문에, 기존의 순수한 함수영 언어인
LISP 계열의 언어와는 조금 다른 표현법을 가지지만, 기본적으로 함수형 언어의 기본적인 특성을 제공하고 있습니다.

### First class functions

함수형 언어에서 함수는 1, “a” 와 같은 일반적인 값과 다르게 취급되지 않습니다. 함수는 인자로 전달 될 수 있으며, 변수를 정의하듯
함수 안에서 함수를 정의 할 수 있습니다. 이런 점을 통해 함수형 언어에서는 함수를 통해 좀 더 강력하고 표현력 있는 control flow
를 만들어 낼 수 도 있습니다.

Scala에서는 함수를 literal 로 표현 할 수 있으며 이는 강력한 표현력을 제공해 줍니다. “callback” 함수를 정의하기 위해
필요도 없는 익명 객체를 정의하거나 listener type을 별도로 정의할 필요도 없습니다. 함수 자체가 클래스와 동일한 최상위 개념이기
때문이죠.

### Less side effects (Immutable data structure)

또다른 함수형 언어의 가장 큰 특징은 side effect가 없어야 한다는 점입니다. 함수가 인자로 전달 받은 값 이외에 어떠한 상태 변경도
발생하지 않아야 한다는 것입니다. 즉, 전달 받은 값으로부터 연산 결과를 리턴하지만 이 과정에 어떠한 내부 상태도 변경되어서는 안된다는
점입니다.

이미 자바에도 String 클래스의 구현이 그러한데, 기본적으로 모든 operation은 immutable 한 상태를 보장하기 때문에 모든
String class의 함수들은 새로운 값을 리턴합니다.

Scala는 기본적으로 immutable 값을 권장하며 때에 따라서는 변경 가능한 변수를 사용 가능합니다. 즉, 때에 따라서는
명령형(imperative) 스타일로 변수를 사용할 수 있으며, mutable한 상태를 가질 수 있다는 말입니다. 하지만, 이는 명령형
방식에 익숙한 개발자들의 편의 및 특정 상황에서 imperative 스타일이 좀 더 명확할 수 있다는 점에서 제공하는 것이지, 절대로
mutable 변수를 공개하거나 공유하는 것은 피하는 것이 좋습니다.

# Why Scala?

Scala가 어떤 언어인지 간단히 특징들을 살펴 보았지만, 이것만으로 왜 Scala를 써야하는지는 충분치 않을 것입니다. 어떤 특징들이 많은
개발자및 소프트웨어 회사들이 Scala를 선택하게 했는지 설명과 코드를 통해 좀 더 살펴 보도록 하겠습니다.

### Scala is concise

짧은 코드가 항상 간결한 것은 아니지만, 간결한 코드는 짧습니다. 가끔 Scala에 대해 짧게 설명할 필요가 있는 경우,  이해를 돕기 위해
아래와 같은 비유를 들곤 합니다.

“자바로 쓰여진 코드는 대서사시 같지만, Scala는 시와 같다"

간결함과 그를 통한 강력한 표현력은 Scala의 가장 큰 언어적 장점입니다.

* * *

// this is Java

class IndexedString {

    private int index;

    private String string;

    public IndexedString(int index, String string) {

        this.index = index;

        this.string = string;

    }

}

// this is scala

class IndexedString(index: Int, string: String)

* * *

위의 예제는 int 형값인 index 와 string 값을 private 멤버로 가지는 IndexedString 이라는 동일한 클래스를
정의하는 자바와 Scala 코드입니다.

* 세미콜론(;)은 생략 가능합니다. 

자바 코드와 Scala 코드를 비교해보면, 기존에 아무렇지도 않게 열심히 반복하며 작성하던 자바 코드가 얼마나 많은 중복을 가지고 있는지 알
수 있습니다. 클래스 이름은 생성자에서 반복되며 멤버변수 역시 이에 값을 할당해주기 위한 생성자의 지역변수로 반복되고 있습니다. 여긱다가
getter 와 setter 함수를 추가하고자 한다면 얼마나 많은 불필요한 반복이 발생할지 쉽게 예측 가능할 것입니다.

뒤에서 다시 언급하겠지만, Scala의 타입 선언 역시 간결한 방식을 택하고 있습니다. 자바의 타입 표현과 달리 Scala는 타입
추론(type inference) 기능을 가지고 있어 타입 선언시에도 불필요한 반복을 할 필요가 전혀 없습니다. 간단히, “너도 알고 나도
아는 것" 은 언제나 생략 가능합니다.

### Scala is high-level

프로그램의 복잡도를 낮추기 위해서, 추상화를 통한 개념적인 코딩은 개발자에게 상당히 중요한 부분입니다.

문자열의 경우, 말 그대로 문자의 열이기 때문에 String class 는 Character 의 List 로 바라볼 수 도 있어야 합니다.
하지만 아래 예에서 보이듯이 자바에서는 문자열을 다룰때 문자열 그 자체로만 바라보고 절차적으로 코딩을 해야합니다.

* * *

//this is java

boolean hasUpperCase = false;

for (int i = 0; i < string.length(); ++i) {

    if (Character.isUpperCase(string.charAt(i))) {

        hasUppperCase = true;

        break;

    }

}

* * *

문자열을 문자열 그대로 문자 하나씩 방문하며 바깥쪽의 변수에 결과를 직접 저장하며 (side-effect) 수행 후 종료하는 로직까지 직접
작성해야합니다.

이에 반해 Scala에서는, 문자열을 좀 더 고수준으로 character의 sequence 로 바라 볼 수 있으며 어떤 캐스팅이나 명시적
변환 없이 collection library에 존재하는 함수를 그대로 사용가능합니다.

* * *

val hasUpperCase = string.exists(_.isUpper)

* * *

위의 예제에서 보듯이, string 이라는 문자열을 collection 으로 바라보고 collection library에 정의된 exists
함수에 _.isUpper 라는 명제(predicate) 를 전달해 대문자가 존재하는지 여부를 체크할 수 있습니다. String에는
exists 함수가 존재하지 않음에도 위 코드는 잘 컴파일이 되어 실행되며 각 문자열의 isUpper 라는 함수를 호출하여
true/false 여부를 체크합니다.

간단히 설명하자면, String을 Character의 Sequence로 바라 볼수 있다는 rule 이 정의 되어 있으며 컴파일 타임에 이
규칙을 기반으로 컴파일러가 추론을 하여 적절한 타입으로 변환하는 것 입니다.(정확히는, StringOps라는 wrapper class로
둘러싸여집니다.)  좀더 자세한 설명은 함수 literal 표현과 implicit conversion 에서 설명하도록 하겠습니다.

### Scala is statically typed

최근 인기 있는 언어들의 특징 중 하나는 대부분의 언어가 dynamic typed 라는 점입니다. 그럼에도 불구하고 가장 최신 언어중 하나인
Scala는 정적 타입 언어이며, 자바와 같이 모든 타입은 명시되어야 하며, 컴파일 타임에 모든 타입 에러는 검증됩니다. 이에 더 나아가
Scala는 지금까지 언어중 가장 강력한 타입 제한을 하며, 여러 표현법을 통해 타입에 대해 좀 더 자세히 명시할 수  있습니다.

물론 정적 타입이 언어의 장점이라는 부분은 상당한 논쟁을 불러 일으킬 수 있는 부분이지만, 적어도 정적 언어가 refactoring 면이나,
함수의 인자나 객체의 property 등 에 대한 unit test는 필요 없는 점, 때로는 타입 자체가 문서화의 기능도 하고 있다는 점
등은 정적 타입언어의 강점이라고 할 수 있습니다.

기본적인 정적 타입 시스템외에 Scala가 가지고 있는 가장 큰 강점은 바로 타입 추론 입니다. 이를 통해 코드를 좀 더 간결하고 명료하게
만들 수 있습니다.

(때로는 타입 문서화나 컴파일 타임 검증을 위해 일부로 명시하는 경우도 있습니다.)

#### Type inference

Scala에서 모든 타입은 변수나 함수 뒤에  “:” 을  통해 명시하게 됩니다. 자바와 달리 뒤쪽에서 타입을 명시하는 데 이런 방식을
택하는 많은 언어들의 특징은 타입이 생략 가능하다는 점 입니다. Scala 역시 타입을 생략 할 수 있지만, 모든 생략된 타입은 컴파일
타임에 컴파일러에 의해 추론되어 바이트코드로 컴파일 되게 됩니다.

* * *

// generic 타입 생략

val x:Map[Int, String] = new HashMap()

//or

val x = new HashMap[Int, String]

val str = “aaaa”

//리턴 타입 생략

def hasUpperCase(str: String) = str.exists(_.isUpper)

* * *

위의 예제처럼 간단한 경우부터 복잡한 함수 내부의 구현에서도 추론 가능하다면 대부분 생략 가능합니다.

# Scala 설치 및 실행

### Install

Scala는 <http://www.scala-lang.org/downloads> 에서 다운로드 가능하며 간단한 설치 과정을 거친 후

* * *

$ scala

* * *

명령으로 바로 Scala Interpreter 를 실행할 수 있으며, 각 platform 별로 package manager 등을 이용해 설치
역시 가능합니다. 맥의 경우 Homebrew를 사용하고 있다면,

* * *

$ brew install scala

* * *

명령으로 바로 설치 가능합니다.

참고로, 모든 Scala 구성 요소는 자바로 구현되어 있는 jar 일 뿐입니다. 필요한 경우 런타임에서 컴파일러나 인터프리터 라이브리에도
접근 가능합니다.

현재(2012.09.10) Scala의 최신 release 버전은 2.9.2 이며, 최신 개발 버전은 2.10.0-M7 입니다.

### Compile

Scala 의 경우 인터프리터를 제공 하며, 실제 개발 환경에서는 대부분의 경우 SBT(Simple Build Tool) 를 이용하기 때문에
직접 컴파일을 할 일은 별로 없습니다.

직접 컴파일이 필요한 경우 다음과 같이 간단히 compile 가능합니다.

* * *

$ scalac A.scala

* * *

기본적으로 package 구조에 맞춰 디렉토리를 생성하고 따로 설정값을 주지 않는 경우, 현재 디렉토리를 기준으로 하여 class 파일을
저장합니다.

Scala 컴파일러는 많은 일을하고 여러 jar 를 로딩하기 때문에 상당히 느립니다. 좀 더 빠른 실행을 원할 경우 scalac 대신
compiler daemon을 사용하는  fsc (fast scala compiler)  명령을 사용하는 것이 좋습니다.

fsc 는 처음 실행시 컴파일러 데몬을 실행하고, 다음 실행부터는 이 데몬을 재사용하여 컴파일 속도를 크게 향상 시킵니다. 아래 예제에서
보이듯이, 두번째 컴파일부터는 매우 빠른 속도롤 보여줍니다.

* * *

$ fsc -verbose -d /tmp test.scala  
...  
[Port number: 32834]  
[Starting new Scala compile server instance]  
[Classpath = ...]  
[loaded directory path ... in 692ms]  
...  
[parsing test.scala]  
...  
[total in 943ms]  
  
$ fsc -verbose -d /tmp test.scala  
...  
[Port number: 32834]  
[parsing test.scala]  
\&...  
[total in 60ms]  
  
$ fsc -verbose -shutdown  
[Scala compile server exited]

* * *

  
* 실행한 데몬은 -shutdown 명령으로 중단시킬 수 있습니다.

### Scala Interpreter

Scala는 대부분의 최신 언어와 마찬가지로 Interpreter 또는 REPL(Read-Eval-Print Loop) 이라 불리는 콘솔을
통해 간단한 실행및 테스트가 가능합니다.

* * *

$ scala

scala> 1+1

res13: Int = 2

scala> res13 * 5

res14: Int = 10

scala> println(res14)

10

* * *

위의 예제처럼 간단한 연산을 바로 실행 가능하며, 자신의 코드 역시 바로 불러와 테스트 가능합니다.

(물론 자신의 클래스가 classpath 상에 존재해야 하며, import 하거나 full name 을 명시하여 사용 가능합니다.)

## Basics

### Defining variables

Scala에는  “val”과 “var”라는 2가지 타입의 변수가 존재합니다. 전자는 value를 의미하며 말 그대로 값을 선언할 때 쓰이며,
선언 이후에는 변경 불가능 합니다. 후자는 variable을 의미 하며 변경 가능한 변수를 의미합니다. val 로 선언된 변수는 자바의
final 변수와 동일하기 때문에,  단지 참조가 변경 불가능한 것이며 해당 객체의 멤버 변수가 var 로 선언되어 있다면, 당연히 변경
가능합니다.

* * *

scala> val msg = "Hello, World!"

msg: java.lang.String = Hello, World!

scala> msg = "Welcome to Scala!"

<console>:8: error: reassignment to val

       msg = "Welcome to Scala!"

               ^

* * *

위와 같이 val 로 선언된 값에 재할당을 할 경우 컴파일 에러가 발생합니다.

### Block Expression

하나의 표현으로 원하는 값을 나타낼 수 없을때 중괄호({}) 를 이용해 표현식을 묶을 수 있습니다. 묶여진 표현식의 값은 마지막 표현식이
되며, 중간에 어떤 코드가 들어있고 어떤 side effect가 발생했는지는 전혀 상관이 없습니다. 변수이던 함수 이던 함수의 인자이던
상관없이 block expression은 하나의 값을 나타냅니다.

* * *

scala> val a= {

     |println(1)

     |println("a")

     | 5

     | }

1

a

a: Int = 5

scala> a

res1: Int = 5

* * *

### Defining functions

함수의 선언은 def keyword로 시작되며 함수 선언부와 구현 부는 “=” 로 구분됩니다. 마치 수학의 f(x,y) = x +y 와
마찬가지로 말입니다.

* * *

scala> def f(x:Int, y:Int) = x + y

f: (x: Int, y: Int)Int

* * *

수학에서 함수 표현과 다른 점은 def 로 시작해야하며, 인자의 타입을 명시해야 한다는 점 뿐입니다. 위와 같이 선언된 함수는,

* * *

scala> f(1,2)

res0: Int = 3

* * *

이와 같이 사용 가능합니다.

가끔은 Console.println 처럼  “=” 이 사용되지 않고 선언된 함수들이 존재하는데, 이는 리턴값이 Unit(void)인  경우에
해당 함수가 마치 procedure 와 유사하게 보이도록 해주는 문법입니다.

* * *

def printGreetings(name: String) {

    printf("Hello, %s", name)

}

* * *

* printf 함수 역시 존재합니다 :)

함수의 구현 부분이 한개의 표현식으로 쓸 수 없는 경우, 앞에서 언급한 block expression 을 이용할 수 있으며, 당연히 리턴값은
묶여진 표현식의 마지막 값입니다.

### Define anonymous function

Scala에서는 함수 literal 이라 불리는 표현법으로도 함수 선언이 가능합니다.

* * *

scala> (x:Int) => x + 1

res0: Int => Int = <function1>

* * *

아래 결과로 나타난 expression은 다음과 같은 의미를 가집니다.

“res0의 타입은 Int 를 주면 Int 를 반환하는 인자가 1개인 함수이다(function1)”

따라서 res0 를 함수로 사용하여 다음과 같은 호출이 가능합니다.

* * *

scala> res0(3)

res2: Int = 4

scala> res0()

<console>:9: error: not enough arguments for method apply: (v1: Int)Int in
trait Function1.

Unspecified value parameter v1.

              res0()

                     ^

* * *

위 문법을 활용하여 다음과 같이 함수를 인자로 받는 함수에 inline으로 함수를 정의하여 전달 가능합니다.

* * *

scala> List(1,2,3,4).foreach(x=>println(x))

1

2

3

4

* * *

또는 축약형으로 쓸 수 도 있습니다.

* * *

scala> (1 to 10).filter(_ % 2 == 0)

res9: scala.collection.immutable.IndexedSeq[Int] = Vector(2, 4, 6, 8, 10)

* * *

1 부터 10까지의 수 중에서 짝수만을 filtering 하는 코드로,  “_ % 2 == 0” 표현식은 “num => num % 2 ==
0” 의 축약형입니다.

밑줄, “_” 는 함수의 인자가 들어갈 자리라는 뜻이며, 함수 인자가 순서대로 해당 자리에 채워집니다.

참고로,  List 관련 예제는 마치 dynamic typed language 처럼 보여지지만, 내부적으로 다음과 같은 타입 추론 과정을
컴파일 타임에 거치게 됩니다.

1. List 함수는 인자로 전달된 4개의 값의 공통 타입을 추론

2. 멤버들의 타입은 Int로 결정되었으며 전달되는 함수의 인자 역시 Int 여야 함

3. 전달된 함수 x=>println(x) 의 인자 x 의 type이 명시되지 않았기 때문에 Int로 추론

4. 결과 : List[Int](1,2,3,4).foreach( (x:Int) => println(x))

* * *

scala> List(1,2,3,4).foreach((x:String)=>println(x))

<console>:8: error: type mismatch;

 found   : String => Unit

 required: Int => ?

              List(1,2,3,4).foreach((x:String)=>println(x))

* * *

### Type and Generics

Scala의 generics 는 자바와 달리 < > 대신 [ ] 로 표현되며, 객체의 상속관계 등의 상/하 뿐만 아니라 해당 객체가 다른
객체로 변환될 수 있는지, 또는 바라볼 수 있는지 등도 명시가 가능하며 모든 타입 선언은 컴파일타임에 검증 됩니다.

Scala 의 collection library 에는 sum 이라는 함수가 존재합니다. 말 그 대로 collection 안의 데이터를 더하는
함수 인데, 이런 함수가 generic 을 기반으로 하는 collection 에 있을 수 있는 이유는, 간단히 숫자가 아닌 값이 들어 있을
경우 compile 이 되지 않기 때문입니다.

* * *

scala> List(1,2,3,4).sum

res2: Int = 10

scala> List(1,2,3.0,4).sum

res3: Double = 10.0

scala> List(1,"a",3).sum

<console>:8: error: could not find implicitvalue for parameter num:
Numeric[Any]

              List(1,"a",3).sum

* * *

위 예제 처럼 직접 List 를 명시하지 않고 다른 함수로 부터 얻어온 List에 대해서는 어떻게 Compile error 를 발생시킬 수
있는지 의문을 제기할 수도 있습니다. 간단히 설명하자면, 모든 함수는 리턴타입이 명시되어 있고 이를 이용해 판단할 수 가 있습니다. 함수,
변수를 포함한 모든 표현식은 타입을 가지고 있는 값입니다.

심지어는 이런 표현도 가능합니다.

* * *

scala> def getLength[T <: {def length(): Int}](obj: T): Int = obj.length

getLength: [T <: AnyRef{def length(): Int}](obj: T)Int

scala> println(getLength("aaaaa"));

5

* * *

타입 T 는 length() 라는 함수가 있는 클래스의 하위 타입 (<:) 이어야 하며, 이런 표현을 통해  interface 선언 없이도
컴파일타임에 강력한 타입 체킹을 할 수 있습니다.

위의 getLength 함수 호출에서도 보여지지만, 대부분의 경우 type parameter 는 값으로 부터 추론 할 수 있기 때문에 생략
가능합니다.

* Scala에서는 Array역시 함수 처럼 ( ) 사용합니다. ex) Array(1,2,3)(0)  은  1 을 리턴

### Control flow

#### Expression oriented

Scala 대부분의 코드는 문장(statements)이 아닌 표현식(expressions) 입니다. 명령형 언어처럼 절차적으로 명령을 내리는
것이 아닌 모든 표현식은 값을 나타내며, 제어문 조차 값을 나타냅니다.

#### No break

Scala에는 break 문이 없습니다. 대부분의 제어 구조는 함수를 chaining 을 통해 이뤄지며,
map/reduce/filter/collect 등 LISP 등과 유사하게 List Processing 을 통해 원하는 흐름을 만들어냅니다.

#### If / Else

Scala의 if/else 문은 코드를 분기하기 위한 표현이 아니라 조건에 따라 값을 리턴하는 표현식입니다.

* * *

scala> val a = "a"

a: java.lang.String = a

scala> val b = if(a == "a") "b" else "c"

b: java.lang.String = b

* * *

C 계열 언어의 ? 연산자와 비슷한 역할을 하지만, 함수 체이닝을 통해 제어 구조를 완성 할 수 있습니다.

#### For

Scala의 for 문은 자바와 유사한 방식으로 사용되기도 하지만, 일반적으로는 if/else 와 마찬가지로 값을 얻어내기 위해서
사용되어지며 자바와 달리 다양한 조건및 여러 collection 에 대해 한번에 iterating을 할 수 있는 기능을 제공합니다.

* * *

scala> for(n <- 1 to 10) yield n.toString

res3: scala.collection.immutable.IndexedSeq[java.lang.String] = Vector(1, 2,
3, 4, 5, 6, 7, 8, 9, 10)

scala> val a = 1 until 10

a: scala.collection.immutable.Range = Range(1, 2, 3, 4, 5, 6, 7, 8, 9)

scala> val b = 1 to 10

b: scala.collection.immutable.Range.Inclusive = Range(1, 2, 3, 4, 5, 6, 7, 8,
9, 10)

scala> for{

     | n1 <- a

     | n2 <- b if n2 % 2 == 0

     | } yield (n1, n2)

res5: scala.collection.immutable.IndexedSeq[(Int, Int)] = Vector((1,2), (1,4),
(1,6), (1,8), (1,10), (2,2), (2,4), (2,6), (2,8), (2,10), (3,2), (3,4), (3,6),
(3,8), (3,10), (4,2), (4,4), (4,6), (4,8), (4,10), (5,2), (5,4), (5,6), (5,8),
(5,10), (6,2), (6,4), (6,6), (6,8), (6,10), (7,2), (7,4), (7,6), (7,8),
(7,10), (8,2), (8,4), (8,6), (8,8), (8,10), (9,2), (9,4), (9,6), (9,8),
(9,10))

* * *

yield 문을 이용하여 리턴된 값은 전체 iterating 후 적절한 collection에 담겨지며, 위의 예제의 경우
Vector[Tuple[Int, Int]] 타입으로 리턴되었습니다.

If/Else와 For 표현식 만을 가지고 제어 구조를 작성하기에는 부족한 것이 사실입니다. 나머지 부분은 Functional
Combinators를 이용해 쉽게 chaining 가능하며 다른 챕터를 통해 자세히 살펴 보겠습니다.

### Scala scripts

Scala는 컴파일 방식의 언어이지만, 스크립트로서도 사용 가능하며 해당 스크립트는 class 나 main 함수 없이도 바로 작성 할 수
있으며, 전달 인자 역시 args 라는 배열을 통해 바로 접근 가능합니다.

<Args.scala>

* * *

//java style in scala

println("Java Style")

var i = 0

while(i < args.length) {

    println(args(i))

    i += 1 // no ++ operater in scala

}

println("Scala style")

args.foreach(arg => println(arg))

//or

println("Shorthand form, called a partially applied function")

args.foreach(println)

* * *

$ scala Args.scala a b c

Java Style

a

b

c

Scala style

a

b

c

Shorthand form, called a partially applied function

a

b

c

* * *



위 예제에서 첫 번째 방식은 자바 스타일로 var 변수를 사용해서 자바 코드를 그대로 옮겨온 것이며, 두번째와 세번째 방식은 좀 더
Scala 스러운 방식으로 작성한 예제입니다.

* args는 Array 타입으로 Scala에서는 Array 역시 함수이기 때문에 인덱스 값을 함수의 인자처럼 전달하여 해당 인덱스의 값을 얻어옵니다.

# Object-oriented

## Class

Scala의 클래스는 생성자와 접근자를 제외하고는 자바와 거의 유사합니다.

### 접근자 (Access Modifier)

Scala의 접근자는 자바에서의 불편함과 문제점을 해소하기 위해 다음과 같은 다양한 방법을 제공합니다.

  1. public,protected, private 은 inner class 등의 상황을 제외하고는 거의 동일합니다.
  2. private[this] 와 같은 방식으로 this 객체 내부로 접근 제한이 가능합니다.
  3. private[package_name] 방식으로 package private 을 지원합니다.
  4. protected[package_name] 방식으로 package 접근 제한 역시 가능합니다.

### 생성자

첫번째 예제에서 보여졌듯이, Scala는 생성자와 클래스를 동시에 선언합니다. 만약 추가 생성자가 필요하다면, this keyword를
이용해 가능합니다.

* * *

class Rational(n: Int, d: Int) {

    require(d != 0) //if failed, IllegalArgumentException will be raised



    val numer: Int = n

    val denom: Int = d



    def this(n: Int) = this(n, 1) // auxiliary constructor



    override def toString = numer +"/"+ denom



    def add(that: Rational): Rational =

        new Rational(

            numer * that.denom + that.numer * denom,

            denom * that.denom

        )

}

* * *

## Object

Scala에는 static class나 member 가 존재하지 않습니다. 대신에, singleton object 를 지원하며, object
키워드를 통해 선언 합니다. 자바의 static 과 유사하지만, type으로 쓰일 수 없으며 대부분의 경우 val 멤버 변수만을 사용하기
때문에 동시성 문제도 없으며, static 클래스의 초기화 문제도 없습니다.

자바의 singleton object 생성 코드입니다.

* * *

class Singleton{

    private static Singleton instance;

    public void greeting(String name) {

        System.out.println("Hello, " + name);

    }

    private Singleton() {} //prevent constructing from outside

    public static Singleton getInstance(){

        if (instance == null) {

            synchronized(Singleton.class) {  //1

                if (instance == null)          //2

                    instance = new Singleton();  //3

            }

        }

        return instance;

    }

}

* * *

Thread-safe 하게 만들기 위해서 double checked locking 패턴이 이용되었으며 생성자를 private 으로 만들어
외부에서의 생성을 막습니다.

* J2SE 5.0 이후에서는 volatile 을 이용해야합니다.

동일한 역할의 Scala 코드입니다.

* * *

object Singleton {

    def greeting(name: String) {

        println("Hello, " + name)

    }

}

* * *

훨씬 간결하며, 복잡한 생성 과정에서의 동시성 문제도 전혀 없습니다. 타입이 아니기 때문에 생성 역시 불가능하며 사용시에는 그냥 객체 이름을
그대로 접근합니다.

* * *

scala> object Singleton{

     | def greeting(name: String) {printf("Hello, %s", name)}

     | }

defined module Singleton

scala> Singleton.greeting("wangtao")

Hello, wangtao

* * *

또한, companion object 라 불리는 class 와 동일한 이름의 object를 선언하여 factory 용도로 사용하기도 합니다.
일반적으로 여러 생성자를 만들기보다는 이런 형태의 Factory pattern 이 선호 됩니다.

* * *

//in Rational.scala

class Rational(n: Int, d: Int) {

    require(d != 0)



    val numer: Int = n

    val denom: Int = d



    override def toString = numer +"/"+ denom



    def add(that: Rational): Rational =

        new Rational(

            numer * that.denom + that.numer * denom,

            denom * that.denom

        )

}

object Rational {

    def apply(n: Int, d: Int) = new Rational(n, d)

    def apply(n: Int) = new Rational(n, 1)

}

* * *

appy 함수는 해당 객체를 마치 함수처럼 다룰 수 있게 해주는 syntactic sugar 입니다. 다음과 같이 마치 함수를 부르듯 new
키워드 없이 Rational 객체를 생성하고 사용할 수 있습니다.

* * *

scala> println(Rational(2,3))

2/3

* * *

## Trait

Scala 에는 interface나 abstract class 없으며, trait 이 그 역할을 대체합니다. trait 특질, 특성 이라는
의미를 가지는데, 말 그대로 어떤 class 의 부모의 역할을 하기보다는 원하는 특성을 부여하여 기능을 확장시키는 개념으로 이해할 수
있습니다.

OOP의 상속 개념에 대해서 설명할 떄 자주 예로 드는 것이 자동차와 같이 쉽게 분류 가능한 예를 들곤 합니다. 명확한 부모 클래스와
구체적인 자식 클래스로 나뉠 수 있기 때문이죠. 하지만 좀 더 정확히 현실세계를 모델링 하고자 한다면, 다중 상속 개념이 필요 할 수 밖에
없게 되지만 다중 상속의 문제는 너무나 잘 알려져 있고 이를 피하기 위해 많은 프로그래밍 언어들이 선택하는 방법은 바로 mixin 입니다.

Scala 역시 trait 을 이용해 mixin 을 지원하며 클래스 선언시 with 키워드를 이용해 해당 클래스에 원하는 특성을 부여하게
되며, 이런 방식을 통해 코드를 조각 조각 작게 쪼개어 구현할 수 있게 되고 이를 조립하여 원하는 기능의 객체를 만들어 낼 수 있습니다.
바로 Lego style이라 종종 불리는 방식이죠.

* * *

abstract class Person {

    def schedule:Schedule

}



trait Student extends Person {

    private var classSchedule:Schedule = ...

    override def schedule = classSchedule

    def learn() = {...}

}



trait Worker extends Person {

    private var workSchedule:Schedule = ...

    override def schedule = workSchedule

    def work() = {...}

}



class CollegeStudent(school:School, company:Company) extends Student with
Worker {

  // ...

}

* * *

출처: <http://www.codecommit.com/blog/scala/scala-for-java-refugees-part-5>

아래 링크의 좀 더 멋진 예제들 역시 살펴 보시기 바랍니다.

  1. <http://joelabrahamsson.com/entry/learning-scala-traits>
  2. <http://gleichmann.wordpress.com/2009/10/21/scala-in-practice-composing-traits-lego-style/>
  3. <http://www.ibm.com/developerworks/java/library/j-scala04298/index.html>

## Package

package 선언 역시 자바에 비해 유연하며, 다양한 방식을 지원합니다.

아래처럼 자바 스타일이 가장 일반적이며,

* * *

package com.kthcorp

class A

* * *

또는 아래처럼 다양한 방법으로 표현 가능합니다.

* * *

package com.kthcorp

class A

//or

package com.kthcorp {

    class A

}

//or

package com {

    package kthcorp {

        class A

    }

}

//or

package com

package kthcorp

class A

* * *

class 선언 후에도 하위 package 선언 역시 가능하며, 어떤 형식으로 작성 하던 대부분의 경우 문제 없이 컴파일이 됩니다.

참고로, 디렉토리 구조및 파일명을 강제하는 자바와 달리 Scala는 하나의 코드에 여러 클래스를 선언하기도 하며, 디렉토리 구조 역시
소스코드의 경우 지키지 않아도 무방합니다. 컴파일러가 결과물인 class 파일을 적절한 디렉토리에 저장해줄 것이기 때문이죠.

다시 한번 강조하지만, 모든 것은 컴파일 타임에 이루어집니다 :)

## Imports

Scala의 import 문 역시 자바의 그것에 비해 매우 유연하고 강력하며, 다음과 같은 특징을 가지고 있습니다.

  1. 어느 장소에서나 import 가 가능하며, 변수의 scope와 동일한 유효 범위를 가집니다.
  2. aliasing이 가능합니다.
  3. object(singleton 객체)나 package 자체 import가 가능합니다.
  4. “*” 대신 “_” 를 사용합니다.

* * *

scala> :paste

// Entering paste mode (ctrl-D to finish)

object Singleton {

    def greeting(name: String) {

        import java.util.{Date => UtilDate}

        printf("Hello, %s at %s", name, new UtilDate())

    }

}

^D

// Exiting paste mode, now interpreting.

defined module Singleton

scala> import Singleton._

import Singleton._

scala> greeting("wangtao")

Hello, wangtao at Tue Sep 11 14:24:54 KST 2012

* * *

## Implicit Conversion

대부분의 실제 데이터는 하나의 타입 만 으로 모델링 하는 것은 쉽지 않습니다. 개념적으로는 email 같은 경우 문자열로 표현 할 수도
있지만, Email 같은 객체에 담고 언제 든지 문자열로써 사용할 수 있는 것이 더 정확하고 편리할 것입니다. 하지만, 과도한 타입과
객체들은 개발자를 피곤하게 합니다. Type hierarchy를 잘 설계해야 하며, 각 type 에대한 적절한 함수 역시 각각 선언하거나
호출 전에 적절히 변환해야 합니다.

가장 많이 쓰이는 간단한 숫자 하나에도 타입 문제는 골치거리 중 하나 입니다. Int, Double 등 많은 상황에 맞는 효율적인 타입을
쓰는 것은 프로그래밍 언어에서는 당연한 것이긴 하지만, 각 타입별로 함수를 별도로 작성을 해야 하거나 명시적으로 변환하는 함수들을 만들어줘야
하니까요. Dynamic 타입 언어들은 이런 문제를 암묵적인 자동 변환으로 해결합니다. 하지만, 이런 방식은 매우 편리하기도 하지만 디버깅
하기도 쉽지 않은 예상치 못한 문제를 발생시키곤 합니다.

Scala는 이에 대한 해결책으로 하나의 데이터를 여러 데이터로 바라볼 수 있게 (Viewable) 해주는 Implicit
conversion 이라는 기능을 제공합니다. 많이 쓰이는 기본적인 숫자간의 변환같은 것을 제외하고는 명시적으로 선언을 해야만 작동하며 변환
룰을 import 해야만 하기때문에 scope 역시 변수와 마찬가지로 해당 block 안에서만 유효합니다.

엄격한 언어답게 기본적으로 Int 는 Double로 자동 변환 되지만, Double은 Int로 자동 변환 되지 않습니다.

* * *

scala> def printInt(n: Int) { println(n)}

printInt: (n: Int)Unit

scala> printInt(3.0)

<console>:9: error: type mismatch;

 found   : Double(3.0)

 required: Int

              printInt(3.0)

                       ^

scala> def printDouble(n:Double) {println(n)}

printDouble: (n: Double)Unit

scala> printDouble(3)

3.0

* * *

이는 자동 import 되는 scala.Predef object에 해당 변환 룰이 선언되어 있지 않기 때문입니다. 오직 Int 를
Double 로 변환하는 룰만 존재하는 것이죠. 아래는 Predef 객체 일부분인데, 보시다시피 Int 는 Long, Double,
Float로 변환 가능하지만 반대의 경우는 정의가 없습니다.

* * *

object Predef extends LowPriorityImplicits {

    implicit def int2long(x: Int): Long = x.toLong

    implicit def int2float(x: Int): Float = x.toFloat

    implicit def int2double(x: Int): Double = x.toDouble



}

* * *

변환룰은 함수로 정의하며, implicit 키워드를 사용하며 인자의 타입과 리턴타입을 이용해 적용 여부를 검사합니다. 또한, 컴파일 타임에
해당 함수가 현재 scope 안에서 직접 보여야 합니다. 즉, 함수가 같은 scope 내에서 먼저 선언되거나 함수 자체가 직접 import
되어야 합니다.

자신이 직접 implicit 를 선언한 경우 범위안에서는 당연히 컴파일 타임에 변환 함수를 호출하는 로직이 끼워질 것이고, 해당 변환이
필요한 경우 변환 함수를 다른 곳에서 import를 하면 됩니다. 실제 사용 예를 살펴보면 많은 경우 여러 implicit 를 하나의
Implicits 라는 객체에 모아두곤 합니다.

참고로, 해당 객체가 변환 가능한 객체의 함수도 직접 사용이 가능합니다. Int는 Double 로 바라 볼 수 있기 때문에 Double의
모든 함수를 직접 호출 할 수 있으며, 이는 compile time에 conversion을 발생시킵니다.

또한, 아래처럼  “implicit” 키워드는 함수의 인자에도 사용할 수 있습니다. 자동으로 해당 scope 내의 같은 타입의
implicit 로 선언된 변수가 함수 인자로 지정되며, 이는 마치 injection 유사한 개념으로 사용할 수도 있습니다.

* * *

scala> implicit val somethingYouKnowAndIKnow: String = "Java sucks!"

somethingYouKnowAndIKnow: String = Java sucks!

scala> def sayTheTruth(implicit truth: String){println(truth)}

sayTheTruth: (implicit truth: String)Unit

scala> sayTheTruth

Java sucks!

* * *

Scala 에서 제공되는 대부분의 conversion은 변환 자체가 가벼우며 손실이 발생하지 않는 것들만 제공되며, 필요한 경우 직접
작성해여합니다. 단, 자신이 직접 변환룰을 작성할 때는 정확히 이해하고 사용해야하며, 모든 것은 여러분이 구현한 코드에 달려있습니다.
한마디로, Int를  String 으로 변환하거나 String 을 Int 로 변환하는 룰을 추가하지는 마십시요 :)

* 아이러니 하게도 implicit 를 explicit 하게 선언해야 합니다.

## Type hierarchy

![](pubimage?id=1kSNKKKwM8rjGhn9Gnw-
6Q0VCImpwSRZ7_QzwNwXgMxM&image_id=1cHN70Vu8EC4GpKSeycwCCo4uOSimXYY)

그림에서 보이듯이, Scala의 최상위 class 는 Any 이며 값을 나타내는 AnyVal, 참조를 나타내는 AnyRef 가 그 뒤를
잇습니다. Nothing은 bottom type 이라 불리며 모든 타입의 하위 이며, Null 은 모든 참조 타입의 최하위 타입입니다.

# Functional / Collection

## List, Set, Map, Tuple

Scala 의 collection library 에 존재하는 List, Set, Map 등의 자료 구조 클래스는 대부분 abstract
이며, 객체를 얻기 위해서는 별도의 표현법을 사용하거나 factory object를 이용해야합니다.

* * *

scala> val hostPort = ("localhost", 80)

hostPort: (String, Int) = (localhost, 80)

scala> 1 -> 2

res0: (Int, Int) = (1,2)

scala> Map(1->"a", 2->"c")

res4: scala.collection.immutable.Map[Int,java.lang.String] = Map(1 -> a, 2 ->
c)

scala> Set(1,2,3)

res5: scala.collection.immutable.Set[Int] = Set(1, 2, 3)

scala> Set.apply(1,2,3)

res8: scala.collection.immutable.Set[Int] = Set(1, 2, 3)

scala> Array("a",1,2)

res6: Array[Any] = Array(a, 1, 2)

scala> 2 :: 1 :: “bar” :: “foo” :: Nil

res14: List[Any] = List(2, 1, bar, foo)

scala> Set(Map(1->"a"), Array(3,4), List("a","b",10))

res7: scala.collection.immutable.Set[java.lang.Object] = Set(Map(1 -> a),
Array(3, 4), List(a, b, 10))

scala> List(1,2,3).getClass

res13: java.lang.Class[_ <: List[Int]] = class
scala.collection.immutable.$colon$colon

* * *

Tuple 의 경우 별도의 객체 없이 () 로 둘러싸서 표현하며, 별도의 class 선언 없이 논리적으로 연관된 값들을 묶어서 리턴하거나
전달하기 위해서 사용됩니다.

## Option

Option은 일종의 container 로, 어떤 값을 가지고 있거나 가지고 있지 않은 상태를 표현 하기 위해 쓰입니다.

* Haksell 이란 언어의 Maybe 타입에 영향을 받은 것으로 알려져 있습니다.

Option 은 추상 클래스와 유사한, trait 으로 선언되어 있으며 다음과 같은 형식을 지닙니다.

* * *

trait Option[T] {

    def isDefined: Boolean

    def get: T

    def getOrElse(t: T): T

}

* * *



보다시피 아주 간단한 container 역할을 하는 추상 클래스로, Some[T] 와 None을 concrete child class 로
가지고 있습니다.

자바나 C 계열 언어들의 함수는 값을 찾을 수 없는 경우 -1 또는 null 을 리턴합니다. 이런 함수 들의 문제점은 -1 이나 null
같은 값의 해석이 documentation 에 의존해야 하며, -1이나 null 자체가 의미 있는 값일 경우 해결이 불가능해집니다.
Scala 에서는 이 문제 해결을 위해 Option 타입을 제공하며, 존재하는 값을 의미하는 Some 과, 존재하지 않는 값을 의미하는
None 두가지로 표현을 하는 것입니다. 간단히 기존 언어의 -1, null 리턴하는 경우라면 None 을 나머지 경우 Some 을 리턴하면
된다는 말입니다.

Some 을 생성할 경우 실제 값을 전달해야하며, None은 singleton object로 그 자체가 값입니다.

* * *

scala> Option(3)

res10: Option[Int] = Some(3)

scala> Option(null)

res11: Option[Null] = None

scala> Some(null)

res12: Some[Null] = Some(null)

scala> Option(-1)

res13: Option[Int] = Some(-1)

scala> None

res14: None.type = None

scala> val optionalInt: Option[Int] = None

optionalInt: Option[Int] = None

scala> val optionalInt2: Option[Int] = Some(3)

optionalInt2: Option[Int] = Some(3)

* * *

Map.get 함수는 Option을 리턴 타입으로 가집니다. Map 자체에 그 값이 있을 수도 있고 없을 수 도 있기 때문입니다.

* * *

scala> val numbers = Map(1 -> "one", 2 -> "two")

numbers: scala.collection.immutable.Map[Int,java.lang.String] = Map(1 -> one,
2 -> two)

scala> numbers.get(2)

res0: Option[java.lang.String] = Some(two)

scala> val n = if(res0.isDefined) res0.get else "not exists!"

n: java.lang.String = two

scala> numbers.get(3)

res1: Option[java.lang.String] = None

scala> res1.getOrElse("Not defined")

res2: java.lang.String = Not defined

* * *

리턴 받은 Option 객체에서 값을 꺼내기 위해서는 위의 Option trait의 정의에 있는 isDefined 와 get을 쓰거나
getOrElse 를 이용하면 됩니다. 하지만, 좀 더 일반적인 방법은 사이즈가 1인 collection, 즉 monad 로 Option을
바라보는 방식입니다. Monad 부분에서 자세한 설명을 하도록 하겠습니다.

## Functional Combinators

### foreach

side effects 를 발생시키기 위한 용도로만 사용합니다. 리턴값이 값이 없다는 의미의 Unit을 리턴하기 때문에 리턴값은 의미가
없으며, 대부분의 경우 block expression 중간에 잠시 사용되거나 더 이상 값을 리턴할 필요가 없는 부분에서 사용할 수 있습니다.

* * *

val numbers = 1 to 100

val sum = {

    var temp = 0;

    numbers.foreach(n => temp += n)

    temp

}

println(sum)

//물론 테스트 코드가 아닌, 실 환경에서는...

//println(numbers.sum)

* * *

### map / reduce

map 은 함수형 언어에서 가장 널리 쓰이는 함수로,  각각의 멤버를 방문하며 전달 받은 함수를 수행 하여 얻은 결과를 동일한
collection에 저장하는 함수입니다.

이에 반해, reduce는 해당 데이터의 개수를 하나로 합치기 위한 함수로 앞 연산의 결과가 다음 연산으로 전달되며 눈뭉치 처럼 점점
커져가는 방식으로 작동합니다.

* * *

scala> (1 to 10).map(_*2).map(_.toString).reduce(_ + _)

res16: java.lang.String = 2468101214161820

* * *

위 과정은 아래와 같이 설명할 수 있습니다.

  1. 1에서 10까지의 collection 생성 (1 to 10)
  2. 1에서 10까지 방문하며 각 숫자 * 2 실행 ( _ * 2)
  3. 2,4,6,8, …, 20 까지 저장된 10개의 멤버를 모두 문자열로 변경 (_.toString)
  4. 첫 두개의 문자열을 합하고 그 결과를 3번째 문자열과 합하고 마지막 멤버까지 합하기 (_ + _)

이처럼 대부분의 경우 특별한 제어문 없이도 데이터 프로세싱이 가능하며 원하는 결과를 한줄의 function chaining으로 만들어 낼 수
있습니다.

### 그외의 functional combinators

map/reduce 외에도  filter / zip / partition / find / drop / dropWhile / foldLeft
/ foldRight / flatten / flatMap 등의 다양한 함수들이 제공되며 각 함수를 이해하고 적재적소 잘 활용하고 뒤에 나올
pattern matching 까지 사용하면 필요한 모든 제어구조를 표현 할 수 있습니다.

## Monad

Scala 문서를 보다보면 monad (단세포 생물 등), monadic 등의 표현이 자주 나오는데, 간단히 collection 처럼 다룰
수 있는 사이즈가 1인 대상으로 이해하면 됩니다.

대표적으로 Option 객체가 monad 이며 option 객체에는 collection 객체 들과 동일한 map/foreach 등의 함수가
존재합니다. 만약 Option 객체가 None, 즉 사이즈가 0인 collection 이라면, 인자로 전달된

함수들은 실행 되지 않을 것입니다.

* * *

scala> :paste

// Entering paste mode (ctrl-D to finish)

val idToName = Map(

    1->"wangtao",

    2->"tao.kim",

    3->"sangbeom.kim",

    4->"sb.kim"

)

(1 to 10).foreach(id =>

    idToName.get(id).foreach(

        name => println("Hello, "+ name)

    )

)

^D

// Exiting paste mode, now interpreting.

Hello, wangtao

Hello, tao.kim

Hello, sangbeom.kim

Hello, sb.kim

* * *

테스트를 위해 1부터 10까지의 숫자가 담긴 collection 을 만든 후 해당 숫자 값들을 idToName Map을 통해 이름으로
변경하는 코드 입니다.  Map.get 함수가 리턴한 Option을 마치 List 처럼 foreach 함수를 사용하여 담고 있는 값에
접근하고 있으며, 이는 Option 객체를 마치 리스트등의 데이터 구조처럼 다룰 수 있다는 말입니다.

이런 방식의 접근은 데이터를 꺼내와서 값이 있는지 없는지 확인하고 코드를 분기하기 보다는, 값이 있을때 해당 함수가 실행하게 되는 전형적인
functional style로 코드를 작성하게 해줍니다. 실제로도 Option 객체는 List 로 변환 가능하며 Some의 경우 사이즈가
1인 List로 None의 경우 Nil (empty List) 로 변환됩니다.

Option 외에도 기타 프레임웍들이 사용하는 Future 등의 객체도 monad로 다룰 수 있도록 API가 설계되어 있습니다.

## Pattern matching

Scala의 가장 강력하며 유용한 기능 중에 하나인 pattern matching은 간단히 switch case 와 유사한 case by
case 형태의 코드를 작성할 때 매우 유용하며, 다양한 표현법을 이용해 matching 조건을 선언할 수 있습니다.

### Matching on values

값을 matching 하는 경우는 switch case 와 별반 다를 바 없습니다.

* * *

val times = 1

times match {

    case 1 => "one"

    case 2 => "two"

    case _ => "some other number"

}

* * *

### Matching with guards

조건식을 추가하여 matching 할 수 도 있습니다.

* * *

times match {

    case i if i == 1 => "one"

    case i if i == 2 => "two"

    case _ => "some other number"

}

* * *

### Matching on type

값에 따른 분기 뿐 아니라 타입에 의한 분기 역시 가능합니다.

* * *

def bigger(o: Any): Any = {

    o match {

        case i: Int if i < 0 => i - 1

        case i: Int => i + 1

        case d: Double if d < 0.0 => d - 0.1

        case d: Double => d + 0.1

        case text: String => text + "s"

    }

}

* * *

### Matching on class members

객체의 멤버 변수 역시 조건식에서 바로 접근이 가능합니다.

* * *

def calcType(calc: Calculator) = calc match {

    case calc.brand == "hp" && calc.model == "20B" => "financial"

    case calc.brand == "hp" && calc.model == "48G" => "scientific"

    case calc.brand == "hp" && calc.model == "30B" => "business"

    case _ => "unknown"

}

* * *

사실 들여쓰기가 조금 더 깔끔해 보일 뿐 더 if / else 를 쓴 것과 별차이가 없습니다. 이런 경우에는 바로 다음에 설명할 case
class 라는 방식을 이용하는 것이 훨씬 코드를 간결하게 만들 수 있습니다.

### Case Classes

case class 는 pattern matching 을 지원해주는 class 형태로 일반적으로 자바에서 value object 나
model 이라 불리는 객체들을 주로 case class 로 선언하게 됩니다.

case class 로 선언된 class는 자동으로 factory 함수가 제공되며, equality 와 toString 등의 기능 역시
제공됩니다.

* * *

scala> case class Calculator(brand: String, model: String)

defined class Calculator

scala> val hp20b = Calculator("hp", "20b")

hp20b: Calculator = Calculator(hp,20b)

scala> val hp20B = Calculator("hp", "20b")

hp20B: Calculator = Calculator(hp,20b)

scala> hp20b == hp20B

res39: Boolean = true

* * *

하지만, case class 의 강력함은 생성의 편리함이나 toString, equality 등에 있지 않습니다. 바로 아래 예제와 같은
pattern matching 입니다.

* * *

def calcType(calc: Calculator) = calc match {

    case Calculator("hp", "20B") => "financial"

    case Calculator("hp", "48G") => "scientific"

    case Calculator("hp", "30B") => "business"

    case Calculator(ourBrand, ourModel) => "Calculator: %s %s is of unknown
type".format(ourBrand, ourModel)

}

* * *

class를 생성하는 함수를 그대로  조건식의 표현으로 사용하여 matching 이 가능합니다. 이때 생성함수의 인자에 임의의 변수 이름을
지정하여 해당 값을 추출하여 사용할 수 있습니다. 위의 예에서는 마지막 case 의 ourBrand와 ourModel 변수를 타입 등의
거추장스러운 표현 없이 바로 매칭되는 값에 할당하여 사용할 수 있습니다.

### Extracting pattern

이런 pattern matching 이용해 편하고 깔끔하게 변수 선언을 하는 방법이 있습니다.

* * *

scala> def getLocation = (math.random, math.random)

getLocation: (Double, Double)

scala> val myLoc = getLocation

myLoc: (Double, Double) = (0.24252881689068828,0.17982331409379104)

scala> myLoc._1

res3: Double = 0.24252881689068828

scala> myLoc._2

res4: Double = 0.17982331409379104

scala> val (x, y) = getLocation

x: Double = 0.6297894678697743

y: Double = 0.799919442582773

scala> x

res5: Double = 0.6297894678697743

scala> y

res6: Double = 0.799919442582773

* * *

예제에서 보이듯이 리턴된 tuple을 하나의 값으로 받아 각각 쓰기보다는, 한번에 각 멤버를 extract 할 수 있다는 말입니다. val
(x, y) 표현은 오른쪽에 있는 표현이 tuple 이기 때문에 성립되며,  이런 방식은 List 나 case class 등에 적용 할 수
있습니다.

* * *

scala> val List(a,b) = List(1,2)

a: Int = 1

b: Int = 2

scala> val Calculator(brand, model) = Calculator("myBrand","myModel")

brand: String = myBrand

model: String = myModel

scala> brand

res7: String = myBrand

scala> model

res8: String = myModel

* * *

# Tools & Frameworks

구슬이 서말이어도 꿰어야 보배 라는 말이 있듯이, 아무리 언어가 뛰어나고 훌륭해도 잘 꿰어진 보배가 없다면 별로 쓸모도 없는 언어가 되 버릴
것입니다. 오늘날의 소프트웨어의 규모와 개발 방식을 보면 툴과 프레임웍 같은 도구들 없이는 개발이 힘든 것이 사실 입니다. 또한, 최근
추세를 보더라도 언어 자체를 배우는 경우보다는, 특정 프레임웍을 사용하기 위해 언어를 배우는 경우가 더 많아 보입니다.

스칼라는 출시된지 얼마 안된 언어임에도 불구하고, 이미 다방면에서 널리 쓰이고 있으며 다양한 오픈소스 Tool 들과  Framework 들이
존재 합니다.  어떤 프레임웍들이 널리 쓰이고 있고 어떤 유용한 것들이 있는지, 또한 이 언어가 배울 가치가 있고 현업에서 쓸모가 있는지
확인 하실 수 있도록 빠르게 살펴보도록 하겠습니다.

참고:

  1. <https://wiki.scala-lang.org/display/SW/Tools+and+Libraries#ToolsandLibraries-DevelopmentTools>

## IDE Support

Eclipse와 IntelliJ IDEA 모두 Scala 지원 합니다. 하지만, 빌드툴인 SBT 에 대한 지원이 Maven 만큼 강력하지는
않습니다. 대부분의 경우 SBT 프로젝트에서 IDE 프로젝트를 generate 하는 방식으로, 빌드 파일이 변경될때 마다 IDE 프로젝트
파일들을 다시 만들어줘야 하는 불편함이 있습니다.

  1. Eclipse
  1. <http://scala-ide.org/>
  2. IntelliJ IDEA
  1. <http://confluence.jetbrains.net/display/SCA/Scala+Plugin+for+IntelliJ+IDEA>
  3. Emacs
  1. <https://github.com/RayRacine/scamacs>
  2. <http://www.scala-lang.org/node/354>
  3. <https://github.com/aemoncannon/ensime>
  4. Netbeans
  1. <http://java.net/projects/nbscala>

## SBT (Simple Build Tool)

대부분의 Scala 프로젝트는 SBT 라는 툴을 이용해 project 를 관리합니다. SBT 는 Maven 등과 유사한 툴로서 build
definition을 정의하기 위해 코드와 유사한 DSL (Domain Specific Language) 를 제공하며, 필요한 경우(사실
대부분의 경우) scala 코드를 직접 작성하여 프로젝트의 메타를 정의할 수 있습니다.

라이브러리 의존성 관리를 위해 Ant에서 사용하는 Apache Ivy 를 사용하며 대부분의 경우 Maven과 호환성을 가집니다.

* 사실, Scala의 가장 큰 진입 장벽 중 하나가 SBT 입니다. 너무 유연하고 자유롭게 사용 할 수 있다보니, 어떻게 배우고 써먹어야 할 지 상당히 난감할 수 있습니다. 기본적인 문서를 읽어 보셨다면, 아래 소개하는 여러 프로젝트들의 SBT 스크립트를 살펴 보시기 바랍니다.

참고 :

  1. <https://github.com/harrah/xsbt>
  2. <http://twitter.github.com/scala_school/sbt.html>

##

## ScalaTest

Scala Test Framework 으로  자신에 익숙한 테스트 방식을 선택할 수 있도록 다양한 test suite 를 제공하며
기본적으로는 BDD(Behavior-driven Development) 기반의 test framework 입니다.

다음은 scalatest.org 의 첫 페이지의 소개 예제입니다.

* * *

import collection.mutable.Stack

import org.scalatest._

class StackSpec extends FlatSpec with ShouldMatchers {

    "A Stack" should "pop values in last-in-first-out order" in {

        val stack = new Stack[Int]

        stack.push(1)

        stack.push(2)

        stack.pop() should equal (2)

        stack.pop() should equal (1)

    }

    it should "throw NoSuchElementException if an empty stack is popped" in {

        val emptyStack = new Stack[String]

        evaluating { emptyStack.pop() } should produce
[NoSuchElementException]

    }

}

* * *

참고:

  1. <http://www.scalatest.org/>
  2. <http://en.wikipedia.org/wiki/Behavior-driven_development>

##

## Finagle

최근 Scala 진영에서 가장 왕성한 오픈 소스 활동을 하고 있는 회사는 다름 아닌 Twitter 일 것입니다. Finagle 역시 트위터에
의해 만들어졌으며, 한마디로 말하자면 분산 비동기 RPC 네트웍 스택입니다.

JVM 기반의 클라이언트와 서버 모두 제공 되며 대표적인 주요 기능은 다음과 같습니다.

  1. HTTP/Thrift 등 다양한 통신 프로토콜 제공
  2. Apache Zookeeper 를 이용한  Service Registration/Discovery
  3. Load balancing / Failover 등

수많은 기능을 보유 하고 있지만, 간단히 말하면 원하는 프로토콜로 RPC 통신을 할 수 있도록 Transport layer 에 대한 제반
사항을 Framework 이 제공해 주는 것이며, 개발자는 자신의 로직을 protocol 과 상관없이 독립적으로 구현 하면 됩니다. 현재
트위터 내부적으로 많은 구현들이 Finagle 위에 올려져 있는 것으로 알려져 있습니다.

![](pubimage?id=1kSNKKKwM8rjGhn9Gnw-6Q0VCImpwSRZ7_QzwNwXgMxM&image_id=1
-wKYUDjiI-n2IoXeqknCXJnqMtwP5O4)

<Twitter Service Stack with Finagle>

참고:

  1. <http://twitter.github.com/finagle/>
  2. <https://github.com/twitter/finagle>
  3. <http://engineering.twitter.com/2011/08/finagle-protocol-agnostic-rpc-system.html>

##

## Gizzard

Gizzard 역시 Twitter 가 공개한 오픈 소스 프로젝트로, backend datastore (SQL, Lucene 등) 와 Web
application 사이를 잇는 데이터 분산을 위한 middleware 입니다.

최근 화두로 떠오르고 있는 빅데이터라는 말 자체의 근원중 하나인 트위터가 자신들의 datastore에 사용하던 데이터 분산
로직(sharding or partitioning) 을 별도의 Framework으로 분리한 프로젝트로 데이터 분산을 데이터 베이스 자체 가
아닌 middleware 로 처리하는 Framework 입니다.

![](pubimage?id=1kSNKKKwM8rjGhn9Gnw-
6Q0VCImpwSRZ7_QzwNwXgMxM&image_id=1V5RgTwMCYiI6-gHachIsfNnJpGJJo2E)

참고:

  1. <https://github.com/twitter/gizzard>

## Akka

Actor model 이란 concurrent distributed system 을 만들어 내기 위한 수학적인 추상화 모델로,
Erikson이 Erlang 이라는 언어를 이용해 telecom system을 성공적으로 만들면서 널리 알려 졌습니다.

Akka framework은 Actor model 의 Scala 구현입니다. 임의의 역할 담당하는  Actor 들은 서로 우편을 주고 받듯이
메시지를 주고 받으며 각자 할일을 나누어 동시에 진행 하는 event-driven framework 입니다.

각 Actor 들은 Router 에 의해  묶일 수 도 있으며 Round robin 등의 적절한 strategy를 선택해 일을 할당 받을 수
도 있습니다. 또한 메시지를 주고 받을 때 fire-and-forget 패턴의 tell 방식이나 Promise 패턴을 사용한 ask 방식
모두 지원합니다.

참고로, Scala 자체적으로도 Erlang의 영향을 받은 Actor 모델의 구현을 을 가지고 있지만, 2.10 버전 이후에는 별도의 jar
로 분리되어 deprecate 될 예정이며 Akka 가 그 대체자로 선택되었습니다.

주요 기능:

  1. Scala로 쓰여졌지만, 자바로도 쉽게 사용할 수 있도록 별도의 wrapping api 를 제공
  2. Remote Actor 지원
  3. Supervising, 각 Actor 들은 상위 Actor에 의해 관리됨
  4. Q3 출시 에정인 2.1 버전을 통해 gossip protocol 기반의 위치 투명성을 가지는 Cluster 제공

참고:

  1. <http://akka.io/>
  2. <http://en.wikipedia.org/wiki/Actor_model>

## Play Framework

최근 가장 떠오르는 자바 진영의 웹 프레임웍입니다. 자세한 설명은 봄날은 간다 세션을 참고하세요~

주요 기능:

  1. Akka와 마찬가지로 Java 지원
  1. Rails 스타일의 COC (Convention Over Configuration)
  2. Netty 기반의 비동기 IO 지원
  3. Akka 를 middleware 로 사용할 수 있도록 연동 기능이 제공

참고:

  1. <http://www.playframework.org/>

## Typesafe Stack

Scala의 창시자인 Martin Ordersky 는 2010년 Typesafe 라는 회사를 세우고 Scala 관련 분야에 대해 교육및
컨설팅등의 상업적인 지원을 시작했습니다. 그리고 얼마전 Scala를 기반으로 하고 Akka 2.0 을 event-driven
middleware 로 Play 2.0을 web framework으로 하는 상업적인 지원을 포함한 Typesafe Stack을 발표
했습니다.

참고:

  1. <http://typesafe.com/>

## Spray

Akka 위에 Restful Web Service 를 만들기 위한 framework 으로 Play와 같은 웹프레임웍이라기 보다는 단순히
Akka 위에 REST 스타일 인터페이스를 씌우기 위해 사용됩니다. Play와 Akka 가 Typesafe Stack 으로 묶인지가 얼마
안되서 인지, Play의 Akka 연동 기능보다는 View가 필요없는 REST API 서버라면 현재로서는 Spray 가 훨씬 강력하며 편리해
보입니다.

주요기능:

  1. Asynchronous, Non-blocking IO, Actor 기반으로 수많은 동시 접속 처리 가능
  2. 자체 DSL 지원
  3. REST service에 대한 테스트 용이

참고:

  1. <https://github.com/spray/spray/wiki>

# 글을 마치며

지금 까지 Scala의 주요 기능과 몇몇 툴에 대해서 두서 없이 쭉 훑어 보았습니다.

많은 분들이 아마도 재미도 없고 부족한 설명으로 이해하지 못한 부분들을 뒤로 한 체 여기까지 오셨을 듯합니다. 전부는 이해하지 못했더라도
한번 공부해 보고 싶으신 마음이 들었다면 그것으로 충분합니다. 아래 링크들 참고 하셔서 새로운 언어를 통해 앞으로의 개발자 생명연장의 꿈을
키워 나가시기 바랍니다 :)

Scala 보다 더 어렵다는 Scala 도입을 성공적으로 이루셔서 더 많은 곳에서 Scala 가 쓰이길 바라며 글을 마칩니다.

참고 문헌 및 자료들:

  1. Programming in Scala 2nd Edition
  2. <http://www.scala-lang.org/node/198>
  3. <http://twitter.github.com/scala_school/>
  4. <http://en.wikipedia.org/wiki/Scala_(programming_language)>
  5. <http://twitter.github.com/effectivescala/>

[Google 드라이브](//docs.google.com/)에서 게시-[악용사례 신고 ](//docs.google.com/abuse?id
=1kSNKKKwM8rjGhn9Gnw-6Q0VCImpwSRZ7_QzwNwXgMxM)-5분마다 자동으로 업데이트

