## Interface &  Inheritance


## 상속은 다중상속이 안됨 !

상속을 지원하게 되면 하나의 클래스가 여러 상위 클래스를 상속 받을 수 있다.
이런 특징 때문에 문제가 발생할 수 있는데 주로 '다이아몬드 문제'라고한다.
<div align="center">

![다중상속](https://user-images.githubusercontent.com/86589565/132803862-c47a76a9-9693-4d46-9ce4-13344e3e00d0.png)
</div>

쉽게 설명을 하기 위해 햄버거에 비유를 해보았다. <br><br>

>Me는 점심시간에 햄버거를 먹고 싶어 주변을 둘러보니 가까이 있는 BurgerKing 과 Lotteria가 보인다.Me는 BurgerKing 과 Lotteria중 어느곳을 갈지 고민중이다.
<br>


<br>여기까지 자바코드로 구현을 해보면

```java
public class Hamberger {
	public void choseBerger() {
		System.out.println("Hamberger");
	}

}
public class BurgerKing extends Hamberger {
	@Override
	public void choseBerger() {	
		System.out.println("버거킹 !");
	}
}
public class Lotteria extends Hamberger {
	@Override
	public void choseBerger() {
		System.out.println("롯데리아 !");
	}

}

//Syntax error, insert "ClassBody" to complete ClassDeclaration 에러 발생 !
public class Me extends  BurgerKing, Lotteria{
    @Override
	public void choseBerger() {
		super.choseBerger();
	}
}
```

하지만 인터페이스라면 어떨까?

```java
interface Hamberger {
	public void choseBerger(); 		
}
interface BurgerKing extends Hamberger {
	@Override
	public void choseBerger();
}
interface Lotteria extends Hamberger {
	@Override
	public void choseBerger();

}
interface Me extends  BurgerKing, Lotteria{
    @Override
	public void choseBerger();
}
```

인터페이스는 기능에 대한 부분만 선언을 해두기 때문에 다이아몬드 상속이 되더라도 충돌할수 없다.

여기서 Me는 BurgerKing과 Lotteria중에 어떤 메소드를 실행 시켜야 할지 알수가 없습니다.

[출처 siyoon210 tisory](https://siyoon210.tistory.com/125)



### 추상 클래스 vs 인터페이스<br><br>

#### 추상 클래스<br>

강아지, 고양이 들의 공통점은 무엇일까? 
~~바로 둘다 사랑스럽고 귀엽다는 공통점이 있다.~~
바로 둘다 동물이라는 공통점이 있다.  동물은 구체적은 실체라기 보는 실체들의 공통이 되는 특성을 가지고 있는 추상적인 것이라 볼수 있다.

WHY? 
- 실체 클래스들의 공통된 필드와 메소드의 이름을 통일할 목적이 있다.
  -   실채 클래스를 설계하는 사람이 여러 사람일 경우 필드와 메소드 명이 제각각일 수 있다. 예를 들어 소유자의 이름을 저장하는 필드를 Telephone에서는 owner라고 하고, SmartPhone에서는 user라고 할 수 있다 // Phone이라는 추상 클래스를 만들어 각 Telephone, SmartPhone에 상속을 시키면된다
- 실체 클랫스를 작성할대 시간이 절약된다
  - 공통된 부분을 제외하고 다른점만 실체클래스에 선언하게 되어 코딩을할때 시간이 절약된다 

HOW?
- 클래스 선언에 abstract 키워드를 붙여야한다.
- 메소드의 실행내용이 동일하다면 메소드에도 abstract를 붙여 추상 메소드를 만들수 있다.

단 추상클래스는 new 연산자를 통해서 객체를 만들도 못하고 상속을 통해 자식 클래스만 만들수 있다.

```java
public abstract class Animal{
    public abstract void sound();
}
```


[출처 이것이 자바다](https://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)


### 상속 ? 인터페이스 비슷?

다형성 생성을 위해 상속 과 인터페이스라는 2가지 방법이 있다. 하지만 여기서 개발자라고 하면 애자일 개발로 따져봤을땐 인터페이스가 훨씬 유연하기에 인터페이스로 다형성을 구상하는것이 좋다.

인터페이스를 사용해서 프로그래밍을 하면 구체 클래스를 사용하지 않기 때문에 유연성이 올라가게 된다. 



[출처](https://syundev.tistory.com/225)
