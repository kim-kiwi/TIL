# TIL

## JAVA

**특징:**
 - 플랫폼 독립적이다.
 - C, C++에 비해 쉽다.

### 문법
**주석**
1. // 주석 한 줄 주석처리할 때 사용
2. /* 주석 */ 여러줄 주석처리할 때 사용
3. /** 주석 */ 문서화할 때 사용

**상수**
```java
final type CONST_NAME = value;
```
보통 상수 이름은 모두 대문자로 씀.

**형변환**
더 큰 크기의 타입에서 작은 크기의 타입으로 형변환을 할 땐 명시적으로 해야한다.

**연산자 우선순위**
 - 최우선연산자 ( ., [], () )
 - 단항연산자 ( ++,--,!,~,+/-   : 부정, bit변환>부호>증감)
 - 산술연산자 ( *,/,%,+,-,shift) < 시프트연산자 ( >>,<<,>>> ) >
 - 비교연산자 ( >,<,>=,<=,==,!= )
 - 비트연산자 ( &,|,,~ )
 - 논리연산자 (&& , || , !)
 - 삼항연산자 (조건식) ? :
 - 대입연산자 =,*=,/=,%=,+=,-=

**배열**
```java
// 생성
type[] name = new type[count];
// 접근
name[idx];
// 생성/초기화 동시에
type[] name = new type[]{1,2,3,4,5};
// 2차원
type[][] name = new type[][]{{1,2,3,4,5},{6,7,8,9,10}};
// 2차원 접근
name[idx1][idx2];

// for each (java 1.5+)
int[] iarr = {1,2,3,4,5};
for (int value:iarr) {
    System.out.println(value);
}
```

**클래스**
```java
// 선언
public class ClassName {
    // ...    
}
// 사용
public class CarExam{
    public static void main(String args[]){
        Car c1 = new Car();
        Car c2 = new Car();
    }
}
```

**참조 타입**
클래스, 배열 등등.. 기본 타입 제외 모두
new 키워드 사용.
new는 메모리에 객체를 올려줌.
객체가 메모리에 올라가면 instance.

객체가 저장된 변수는 객체 자체를 담은 것이 아닌 객체의 위치를 가리키는 것.
-> C의 포인터와 비슷함.

**String 클래스**
java에서 아주 많이 쓰이는 클래스.
```java
/*
new 키워드 X
상수 취급
str1과 str2는 같은 instance를 가리킨다.
*/
String str1 = "Hello, String!";
String str2 = "Hello, String!";
/*
new 키워드 O
무조건 instance 새로 만듦
메모리에 올라감
str3과 str4는 다른 instance를 가리킨다.
*/
String str3 = new String("Hello, String!");
String str4 = new String("Hello, String!");

// 문자열 비교
// 기본적으로 String은 객체라서 str1==str2는 객체의 주소를 비교한다.
// 따라서 문자열의 내용을 비교할땐 String의 메서드인 equals을 통해 문자열을 비교해야한다.
if (str3.equals(str4)) {
    System.out.println("같다.");
}
```

**필드, 메서드**
필드: 클래스의 값, 속성 ( 예: name, age )
메서드: 클래스의 행동 ( 예: run(), greet() )
```java
public class Person {
    // 필드 선언
    String name;
    int age;
    // 메서드 선언
    public void greet() {
        System.out.println("Hello");
    }
}
```

**String 클래스의 메서드**
(타입은 추측해서 썼습니다)
 - int length()
 - String concat(String str)
 - String substring(int a, int b), substring(int a)

**scope와 static**
scope: 변수의 사용 가능 범위

static method에서는 global variable이용 불가
-> static global variable은 이용 가능

static variable은 instance로 부터도 접근 가능하나,
클래스로 부터 접근하는게 바람직하다.

**static variable은 인스턴스별로 생성되지 않는다.**

**enum**
```java
enum Gender {
    MALE,FEMALE;
}
```

Enum은 보통 대문자

**메서드 오버로딩**
매개변수의 유형과 개수를 다르게 하여 같은 이름의 함수를 여러개 쓸 수 있음.

클래스의 생성자 또한 오버로딩 가능

this()를 통해 자기 자신의 생성자를 호출할 수 있다
