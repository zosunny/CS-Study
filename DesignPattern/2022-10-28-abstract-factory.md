> **Abstract Factory**
 is a creational design pattern that lets you produce **families of related objects** without specifying their concrete classes.
> 

- 서로 **연관된 객체들의 집합(families)**을 생성하는 인터페이스를 제공하는 패턴
    
    → 일관된 방식으로 객체들의 집합을 생성
    
- `factory method pattern`을 더 캡슐화한 패턴

- Singleton, factory method pattern 사용

## 구조

![image](https://user-images.githubusercontent.com/72663337/198871032-5ce13d81-0b77-4b5c-87cf-1cf570f2bdb8.png)



1. AbstractProduct
    - Product의 공통 인터페이스
2. ConcreteProduct
    - ConcreteCreator에서 생성되는 구체 Product class
3. Creator interface
    - 객체를 생성하는 메서드들을 공통으로 정의하는 인터페이스
4. ConcreteCreator
    - 구체적인 팩토리 클래스. 내부 구현을 통하여 어떤 타입의 Concrete Product가 생성될지 결정됨
5. Client

## 예제

```java

//Creator interface
public interface FurnitureFactory{
	Chair createChair();
	CoffeeTable createCoffeeTable();
	Sofa createSofa();
}

//Concrete Creators
public class ModernFurnitureFactory implements FurnitureFactory{
	...
	@Override
	public Chair createChair(){
	/** Modern Chair return **/
	}

	@Override
	public CoffeeTable createCoffeeTable(){...}
	@Override
	public Sofa createSofa(){...}
}

public class VictorianFurnitureFactory implements FurnitureFactory{
	...
	@Override
	public Chair createChair(){
		/** Victorian Chair return **/
	}

	@Override
	public CoffeeTable createCoffeeTable(){...}
	@Override
	public Sofa createSofa(){...}
}
```

```java
//Abstract Product
interface Chair{
	boolean hasLegs();
	void sitOn();
}

//Concrete Products
public class VictorianChair implements Chair{
	...
	@Override
	boolean hasLegs(){...}
	@Override
	void sitOn(){...}
}

public class ModernChair implements Chair{
	...
	@Override
	boolean hasLegs(){...}
	@Override
	void sitOn(){...}
}

... Sofa, CoffeeTable 동일
```

```java
//Client
public class Application{
	private FurnitureFactory factory;

	//런타임 시점에 factory를 주입받도록 하는 방식을 사용할 수 있음
	public Application(FurnitureFactory factory){
		this.factory = factory;
	}
	
	factory.createChair();
	factory.createSofa();
	factory.createCoffeeTable();
}
```

→ 같은 인터페이스를 통하여 객체들의 집합을 생성

### Q.

- factory method pattern과의 차이점
    1. inheritance를 사용하는 factory method pattern 과는 다르게
        
        composition 사용
        
    2. 연관된 **여러 종류의 객체**를 생성하기 위해 사용됨
    
    [https://whereami80.tistory.com/211](https://whereami80.tistory.com/211)
    

### Reference

[https://refactoring.guru/design-patterns/abstract-factory](https://refactoring.guru/design-patterns/abstract-factory)
