> **Composite**
 is a structural design pattern that lets you compose objects into **tree structures** and then work with these structures as if they were individual objects.
> 

→ 객체들을 `트리 구조`로 구성하여, 개별적인 객체인 것처럼 동작하게 하는 구조 패턴

여러 개의 객체들로 구성된 복합 객체(전체)와, 단일 객체(부분) 사이의 구별 없이 다룰 수 있게 하는 패턴(구조 패턴 중 하나)

→ 전체와 부분을 구별하지 않고 하나의 인터페이스로 다룸

전체-부분의 관계(ex : Directory-File, Tree)를 갖는 객체 사이의 관계를 보일 때 유용함.

![Composite Pattern](https://user-images.githubusercontent.com/72663337/195846649-fd1aef06-7e50-4fa4-a6d9-ddefda386231.png)


`Composite Pattern`


1. Base Component
    
    Leaf, Composite 클래스의 공통 인터페이스를 정의
    
    → 트리 구조의 전체, 부분 객체들의 공통점을 정의하고 있다.
    
2. Leaf Object
    
    부분 클래스
    
    → leaf node처럼, 자식을 갖고 있지 않음
    
3. Composite(Container) Object
    
    복합 클래스
    
    여러 개의 Component를 자식으로 가짐(Leaf, Composite..)
    
    - Composite는 자식 클래스의 정확한 정보를 알 수 없음(leaf인지, composite인지)
        
        → Component interface를 통하여 자식 원소들이 동작하고 있기 때문
        
    
    여러 자식 객체들에게 작업을 위임할 수 있다.
    

## 예제

![example](https://user-images.githubusercontent.com/72663337/195846966-283f4be1-6182-4597-a495-0a21137ad782.png)


`(https://refactoring.guru/design-patterns/composite)`

**Component interface**

```java

interfactor Graphic{
	void move(int x,int y);
	void draw();
}
```

**Composite**

```java
class CompountGraphic implements Graphic{
	**private List<Graphic> children = new ArrayList<>();**
	
	public void move(int x,int y){
	...
	}
	
	public void draw(){...}

	public void add(Graphic child){...}
	public void remove(Graphic child){...}
}
```

**Leaf**

```java
class Dot implements Graphic{
	int x;
	int y;

	public Dot(int x,int y){...}

	public void move(int x,int y){
	...
	}
	public void draw(){...}
}

class Circle extends Dot{
	double radius;
	
	public Circle(int x, int y, double radius){...}

	@Override
	public void draw(){...}
}
```

 

**Client**

```java
public class ImageEditor{
	public static void main(String[] args){
		List<Graphic> graphics = new ArrayList<>();

		graphics.add(new Dot(1,2));
		graphics.add(new Circle(5,3,10));

		//Dots, Circle을 포함
		CompoundGraphic compounds = new CompoundGraphic();
		compounds.add(new Circle(4,1,15));
		compounts.add(new Dot(1,1));
		graphic.add(compounds);

		//graphic(dot, circle, compounds..) draw
		for(Graphic graphic : graphics){
			graphic.draw();
		}		
	}
} 
```

### Q. 💡 적용하기에 적합한 상황

1. 객체들을 `트리 구조`로 구성해야할 때
2. 복합 객체, 단일 객체를 **동일하게 다루**고자 할 때

### Reference
(https://refactoring.guru/design-patterns/composite)
