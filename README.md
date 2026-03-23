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

this()를 통해 자기 자신의 생성자를 호출할 수 있다.

Car를 생성하는 Car를 생성하는 Car를 생성하는 Car를 생성하는...(Stackoverflow)

**상속**
```java
public class Car {
}

// Car를 상속
public class Bus extends Car {
}
```

**접근 제한자**

접근 제한자는 변수, 상수, 클래스, 메서드, 속성 등에서 쓸 수 있다.
```java
public // 어떤 클래스든 접근 가능
private // 본인만 접근 가능
proetected // 본인, 그리고 상속받은 자식 클래스에서도 접근 가능
// 접근제한자를 적지 않으면 같은 패키지 내에서만 접근 가능
```

**추상 클래스 & 메서드**

추상 클래스는 인스턴스를, 추상 메서드는 내용을 가질 수 없다..
```java
// 추상 클래스는 new Bird(); 같은거 안됨..
public abstract class Bird {
    public abstract void sing(); // 상속 받은 녀석이 구현
    public void fly() {
        System.out.println("날다.");
    }
}

// 추상 메서드들을 모두 구현하지 않으면 Duck도 추상 클래스로 간주됨..
// 지금 상황에서 Duck은 실체가 있는 클래스임. new Duck(); 가능
public class Duck extends Bird {
    @Override // 부모 재산 안전하게 가로채기
    public void sing() {
        System.out.println("노래하다.");
    }
}
```

**super와 부모 생성자**

```java
public class Car{
    public Car(){
        System.out.println("Car의 기본생성자입니다.");
    }
}

public class Bus extends Car{
    public Bus(){
        System.out.println("Bus의 기본생성자입니다.");
    }

}

// new Bus(); 하면 Car()와 Bus()가 둘 다 실행됨. 장유유서가 있다..
```

```java
public class Bus extends Car{
    public Bus(){
        super(); // 부모의 this를 호출하는 것과 비슷함. 어.. 자식이 부모를 낳는다..?
        System.out.println("Bus의 기본생성자입니다.");
    }
}
```

`super()`는 부모 생성자의 매개변수 개수와 자식 생성자의 매개변수 개수가 다를때 유용하다.

**메서드 오버라이딩**

자식 클래스가 부모 클래스가 만들어둔 메서드를 덮어버릴 수 있다. ~~불효자~~

super().method()로 덮어진 부모의 메서드도 다시 쓸 수 있긴 하다.

**클래스 형변환**

자식 클래스를 부모 클래스처럼 다룰 수 있다.
```java
public class BusExam {
    public static void main(String args[]){
        Car car = new Bus();
        car.run();
        car.ppangppang(); // 컴파일 오류 발생
    }
}
```
~~자식의 잠재력을 다 망쳐버리고 있잖아! 넌 전혀 빵빵하고있지 않아!!~~

```java
public class BusExam {
    public static void main(String args[]){
        Car car = new Bus();
        car.run();
        Bus bus = (Bus)car;
        bus.ppangppang(); // 빵빵!
    }
}
```
다시 자식의 잠재력을 발휘시킬 수도 있다.

`car.getClass().getName()`으로 클래스의 이름을 가져올 수 있다. 만약 Car car가 사실은 Bus였다면 "Bus"를 반환한다.

클래스 형변환은 상속관계에 있을때에만 가능하다.

**인터페이스**

TV의 사용법 같이 그냥 사용 설명서라고 보면 될 듯 하다.

```java
public interface TV {
    public int MAX_VOLUME = 100; // 인터페이스에 정의한 변수는 상수다! (변경 불가)
    public int MIN_VOLUME = 0;

    public void on();
    public void off();
    public void volume(int volume);
    public void channel(int channel);
}
```

```java
public class LedTV implements TV { // LedTV 객체에 TV 사용법을 그대로 사용할 수 있다는 뜻인 듯.
    public void on(){
        System.out.println("켜다");
    }
    public void off(){
        System.out.println("끄다");   
    }
    public void volume(int value){
        System.out.println(value + "로 볼륨조정하다.");  
    }
    public void channel(int number){
        System.out.println(number + "로 채널조정하다.");         
    }
}
```

~~전기세 낭비~~
```java
TV tv = new LedTV(); // 객체를 interface로 형변환할 수도 있다.
tv.on(); // TV 인터페이스에 나와있는 메서드, 속성만 사용 가능하다.
tv.off();
tv.on();
tv.off();
tv.on();
tv.off();
tv.on();
tv.off();
```

```java
public interface Calculator {
    public int plus(int i, int j);
    public int multiple(int i, int j);
    default int exec(int i, int j){      // 메서드에 기본값을 넣어놓을 수 있다. 이러면 abstract 아닌건가
        return i + j;
    }
    public static int exec2(int i, int j){   // static 메소드 또한 선언 가능하다. Calculator.exec2로 호출할 수 있는 걸 보아 인스턴스가 아닌 클래스의 메서드인 듯.
        return i * j;
    }
}
```

**중첩 클래스 || 인스턴스 클래스**

```java
public class InnerExam1{ // 클래스 안에.. 클래스 안에.. 클래스 안에.. 클래스 안에.......
    class Cal{
        int value = 0;
        public void plus(){
            value++;
        }
    }

    public static void main(String args[]){
        InnerExam1 t = new InnerExam1();
        InnerExam1.Cal cal = t.new Cal(); // 문법 신기하네
        cal.plus();
        System.out.println(cal.value);
    }
}
```

**정적 중첩 클래스 || static 클래스**

```java
public class InnerExam2{
    static class Cal{
        int value = 0;
        public void plus(){
            value++;
        }
    }

    public static void main(String args[]){
        InnerExam2.Cal cal = new InnerExam2.Cal(); // InnerExam2이라는 클래스의 속성 판정이 된 듯??
        cal.plus();
        System.out.println(cal.value);

    }
}
```

**지역 중첩 클래스 || 지역 클래스**

```java
public class InnerExam3{
    public void exec(){
        class Cal{
            int value = 0;
            public void plus(){
                value++;
            }
        }
        Cal cal = new Cal(); // 영역 안에서만 사용 가능한 클래스라니..
        cal.plus();
        System.out.println(cal.value);
    }


    public static void main(String args[]){
        InnerExam3 t = new InnerExam3();
        t.exec();
    }
}
```

**익명 클래스**

```java
public abstract class Action{
    public abstract void exec();
}

public class ActionExam{
    public static void main(String args[]){
        Action action = new Action(){ // 한 번 쓰고 버리는 클래스 불쌍하다.. 하지만 유용하죠?
            public void exec(){
                System.out.println("exec");
            }
        };
        action.exec();
    }
}
```

**예외**

```java
public class ExceptionExam {
    public static void main(String[] args) {
        int i = 10;
        int j = 0;
        try{
            int k = i / j;
            System.out.println(k);
        }catch(ArithmeticException e){ // 0으로 나눌 때 발생하는 예외를 프로그램을 터트리지 않고 처리하는 모습..
            System.out.println("0으로 나눌 수 없습니다. : " + e.toString());
        }finally {
            System.out.println("오류가 발생하든 안하든 무조건 실행되는 블록입니다."); // 무조건 실행되는 좀비같은 코드 블록.. 든든하다
        }
    }
}
```

**throws**

~~책임전가 ㄷㄷ 무섭다~~
```java
public class ExceptionExam2 {

    public static void main(String[] args) {
        int i = 10;
        int j = 0;
        int k = divide(i, j);
        System.out.println(k);
    }

    public static int divide(int i, int j) throws ArithmeticException{ // 오류처리 "해줘"
        int k = i / j;
        return k;
    }
}
```

**throw**

~~모든 문제를 일으키는 녀석~~
```java
public class ExceptionExam3 {
    public static void main(String[] args) {
        int i = 10;
        int j = 0;
        int k = divide(i, j);
        System.out.println(k);      
    }

    public static int divide(int i, int j) throws IllegalArgumentException { // 경고: 오류 뱉을거임
        if(j == 0){
            throw new IllegalArgumentException("0으로 나눌 수 없어요."); // 오류 뱉어버리기
        }
        int k = i / j;
        return k;
    }
}
```

**custom 재앙**

사용자 입맛에 맞춰 재앙을 꾸밀 수 있다.
```java
public class BizException extends RuntimeException { // 비즈니스적으로 재앙이 일어났을 떄 사용할 듯 하다.
    public BizException(String msg){
        super(msg);
    }       
    public BizException(Exception ex){
        super(ex);
    }
}
```

Method를 Programmers에서는 메소드라고 부르긴 하는데 ~~알빤가요~~

## 객체지향

**추상화**
대상에게 핵심적인 특징만 추출하는 것

**상속**
부모 클래스의 속성과 메서드를 자식 클래스가 물려받아 재사용하는 것

**다형성**
하나의 객체나 메서드가 여러 가지 형태를 가질 수 있는 능력

**캡슐화**
데이터와 그 데이터를 처리하는 기능을 하나로 묶고 실제 구현을 숨겨 외부에서의 직접적 접근을 제한하는 것

## HTTP/HTTPS

**Hyper Text Transfer Protocol**

html, 이미지, 영상 등 웹 콘텐츠를 주고받기 위해 사용하는 통신 규약

https의 s는 secure. 즉 더 안전하다. 암호화를 사용하여 서버와 클라이언트 사이를 오가는 데이터를 엿보기 힘들다고 한다.

### HTTP Method
 - GET: 리소스 조회할 때 씀. url/cat.png 같은 느낌인듯
 - POST: 데이터 처리할 때 씀. `글 써주세요` 하고 요청 보내는 그런거인 듯
 - PUT: 리소스 덮어쓰기. 말 그대로 보내준 리소스로 서버의 리소스를 덮어쓰는 듯. 위험한 거 아닌가??
 - PATCH: 리소스 일부 변경. DB에서 사용자 이메일 부분만 수정할 때 처럼 일부 리소스 변경할 때 쓰는 듯.
 - DELETE: 리소스 삭제. 말 그대로
 - HEAD: GET. 근데 Body가 없음
 - OPTIONS: 리소스에 대한 통신 가능 메서드를 설명(서버에서 보내주는 형식인 듯 하다)
 - CONNECT: HTTPS에서 암호화 터널을 설정하는데 사용한다고 함
 - TRACE: 디버그용 통신. 루프백 테스트를 한다고 함. 보안 위험 있음..

**멱등성**: 여러번 같은 신호를 보내도 결과가 같음.

`GET,PUT,PATCH,DELETE,HEAD,OPTIONS`

### HTTP Status codes
 - 1XX: 정보 제공
 - 2XX: 성공
 - 3XX: 리다이렉션
 - 4XX: 클라이언트측 에러(프론트 갈구라는 뜻)
 - 5XX: 서버측 에러(백엔드 갈구라는 뜻)

### HTTP의 무상태성
저번에 서버에 요청 보냈던 놈이 누군지 기억 못한다는 뜻.
서버 확장에 용의하나, 로그인 같은 서비스에는 쿠키, 세션같은 추가 보안 시스템이 필요해짐.
