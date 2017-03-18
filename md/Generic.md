# 제네릭
실수를 줄이고 편하게 사용하기 위해 제네릭을 사용한다.

```
제네릭 - > 일반적인
제네릭 클래스를 제작한다.
```

* object
>* 사과박스
>* 오랜지박스


* generic
> 1


상위제한 하위제한

# 제네릭 클래스
맴버변수의 클래스 타입을 생성 시에 정해 줄수 있다.
```
public class FruitBox <T>{

	private T fruit;
}
-------------------------------
FruitBox<Apple> applebox = new FruitBox<Apple>();
FruitBox<Orange> orangebox = new FruitBox<Orange>();
```

# 제네릭 메소드
매소드의 반환형태, 매개변수 형태를 매소드 호출시에 정해 줄 수 있다.
```
public <K> K foo(K k){
		return k;
}

System.out.println(myGeneric.foo(new Apple()));
System.out.println(myGeneric.<Integer>foo(123));
```
