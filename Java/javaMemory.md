
## JavaDataType<br><br>

![자바데이터 타입](https://user-images.githubusercontent.com/86589565/132116007-1f48a018-f05d-4d10-9ce1-d7534edcfa55.png)

<br><br>
참조 타입를 이용해서 선언된 변수는 메모리의 번지를 값을 갖는다

```java
// [기본 타입 변수]
int height = 180;
long money = 10000;

//[참조 타입 변수]
String nickName ="Jerry";
String favoriteFood = "Emmental";
```
<br>

![힙스택메모리저장](https://user-images.githubusercontent.com/86589565/132116554-b67104be-8129-4a42-a96c-45ae752d56c2.png)
<br>
<b><u>money</u></b> 와 <b><u> height</u></b> 변수는 stack area에 직접 저장이 되고 있지만 String 클래스의 변수인 <b><u>nickName</u></b>과 <b><u>favoriteFood</u></b> 은 stack area에서는 객체 주소값을 가지고 있다.
<b><u></u></b><br>


## 메모리 사용 영역

<div align = "center">

![Runtime Data Area](https://user-images.githubusercontent.com/86589565/132117417-3fe2694e-f83c-4eeb-be44-29172f8e7d91.png)

</div>

### Method Area<br><br>

클래스(class)들을 로더로 읽어 클래스별로 런타임 상수풀, 필드, 생성자 등 분류해서 저장합니다. JVM이 시작할때 생성되고 모든 스레드가 공유하는 영역입니다.

<br>

### Heap Area<br><br>

객체와 배열이 생성되는 영역입니다. 스택 영역의 변수나 다른 객체의 필드에서 참조합니다. 만약 아무것도 사용이 되지 않는다면 쓰레기로 간주 되어 JVM에서는 쓰레기 수집기 <u><b>(Garbage Collector)</b></u>를 실행시켜 쓰레기 객체를 힙 영역에서 자동으로 제거합니다. <br>
:bookmark_tabs: 사실 자바에서는 코드로 객체를 제거하는 방법을 제공하지 않는다.

<br>

### JVM Stack Area<br><br>

각 스레드 마다 스택영역이 하나씩 존재하며 스레드가 시작될때 할당됩니다.
JVM 스택은 메소드를 호출할때 마다 프레임을 추가 하고 메소드가 종료 되면 해당 프레임을 제거하는 동작을 수행합니다. 

```java
int viewLike = 0;       //  Stack 영역{ viewLike }

if (viewLike ==0){       // Stack 영역 { viewLike, beom, num }
    char beom = 'G'
    double num = 7.8;
}

boolean trueOrFalse = true; // Stack 영역 { viewLike trueOrFalse }
// beom과 num은 if문을 빠져나오면서 소멸됨
```

### NullPointerException

<br>

```java
int[] goArray = null; //참조타입 변수가 null 을 가지고 있을 경우 참조 타입 변수 사용 X
goArray[0] = 100; // NullpointerException 
```
<br>
:bookmark_tabs:  참조 타입 변수를 null로 지정하여 변수를 참조하는 객체가 없기에 애러 발생
<br>

### String Type<br>

```java
String nickName1 = "Jerry";
String nickName2 = "Jerry";
```
<br>
<div align = "center">

![String1](https://user-images.githubusercontent.com/86589565/132118101-0b76c882-46fd-4240-8e53-74aa960c3667.png)
<br>
</div>
문자의 리터럴이 동일하다면 String 객체를 공유하도록 되어 있다.  즉 nickName1과 nickName2는 같은 String 객체를 참조하게 된다.<br>

```java
String nickName1 = new String("Jerry");
String nickName2 = new String("Jerry");
```
<br>
<div align = "center">

![String2](https://user-images.githubusercontent.com/86589565/132118106-8ef28cc5-baf8-4d39-b570-852664cb68ed.png)
</div>
<br>

하지만 new 연산자는 Heap영역에서 새로운 객체를 만들어 서로 다른 String 객체를 참조할 수도 있다. String의 <br>문자열을 비교할땐

```java
boolean beom = str1.equals(st2); // 결과값은 true or false
```

new 연산자를 사용 안할경우는 기존 ( == )을 사용해서 비교가 가능하지만 new 연산자를 사용할 경우 비교하고 싶을땐 equals를 사용해야함

```java
String cat = "Tom";
cat = null;   //참조를 읽은 String 객체는 힙영역에 JVM이 Garbage Collector를 구동시켜 메모리에서 자동 제거한다.
```
<br>

### Array Type<br>

Java에서 배열을 선언할때두가지 형태로 만들수 있다<br>
```java
String[] nickName1;
String nickName[];
```
배열에 값의 목록이 있다면 간단한 배열 객체를 만들수 있다.
```java
String[] nickName = {"Jerry","Tom","SpikeDog"}; 
/*
String[] nickName;
nickName = {"Jerry","Tom","SpikeDog"};  컴파일 애러가 남
*/
```

만약 배열을 먼저 생성하고 나중에 추후에 값을 넣어주고 싶으면 new연산자를 활용하먄됨

```java
String[] nickName = null;
nickName = new String[] {"Jerry","Tom","SpikeDog"};
```
문자열을 정수로 변환하고 싶을땐
```java
Stirng money = "10000";
int realMoney = Integer.parseInt(money);
// Integer.parseInt로 인해 정수로 변환하고 realMoney 변수에 저장한다.
```

다차원 배열일 경우에는
```java
int[][] money = new int[2][3]; // 2X3 인 표가 생성된다고 생각하면됨
//숫자를 있는 그대로 표현하고 싶으면 "+변수명+"을 하면댐
```
배열은 한번 생성하면 크기를 변경할수 없기 때문에 더 많은 저장 공간이 칠요하다면 보다 큰 배열을 새로 만들고 이전 배열로부터 항목 값들을 복사해야함.
<br>

```java
//System.arrycopy( 원본배열, 시작번수, 새로운배열, 시작번수, 원본배열 길이);
String[] helloArray = {"Jerry","Tom","SpikeDog"};
String[] byeArray = new String[6];

System.arraycopy(helloArray, 0, byeArray,0, helloArray.length);
// byeArray = ["Jerry","Tom","SpikeDog",null,null,null] 참조복사 주소가 옮겨짐
```
향상된 반복문<br>
```java
public static void main(String[] args) {
		int[]money = {10000,20000,30000};
		int sum =0;
		
		for (int mo : money) {    // 값에 직접 할당하고 반복함
			sum = sum + mo;
		}
		System.out.println(sum);
	}
```

### 열거타입<br>

열거타입이란?<br>
- 요일에 대한 데이터 (월,화,수,목,금,토,일)
- 계절에 대한 데이터 (봄, 여름, 가을 ,겨울)
- 등등..

한정된 값을 갖는 데이터 타입을 갖는것이다.
<br><br>
열거타입을 선언하기 위해서는 먼저 타입의 이름을 정하고 열거 타입 이름으로 소스 파일을 생성해야댐

```java
Week.java  //이런식으로
```
그 다음엔 public enum으로 작성해야한다.

```java
public enum Week{
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
//관례적으로 열거 상수는 모두 대문자로 작성해야함
// 생성하는 방법은 [ File -> New -> Enum ]으로 작성해야함 사용할때에는
Week today= Week.SUNDAY;
//이런식으로 변수를 적용하고 사용해야함즉 today와 메소드 영역에 있는 Sunday는 같은 참조 값을 가지게 된다.
```
<br>

[출처 이것이 자바다](https://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)

