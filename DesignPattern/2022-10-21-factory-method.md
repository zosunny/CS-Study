> **Factory Method**
 is a creational design pattern that **provides an interface for creating objects** in a superclass, but allows subclasses to alter the type of objects that will be created.
> 
- 객체를 `**생성**`하기 위한 인터페이스를 제공하는 디자인 패턴
- 생성된 객체의 타입은 서브클래스에서 결정할 수 있음 → `인스턴스의 생성을 서브 클래스에 위임`
- 새로운 클래스가 추가되더라도 코드의 수정이 일어나지 않음(`OCP 원칙`)

> Product 타입의 객체를 생성하는 인터페이스를 creator에서 제공
> 
![image](https://user-images.githubusercontent.com/72663337/197338503-290663d4-4da2-4cb5-a622-9ee5042a764b.png)


1. Product interface
    - concrete product들의 interface
2. Concrete Products
    - Product interface의 구현체
3. Creator
    - factory method를 정의하고, 만든 product 객체를 반환함(반환 타입은 Product interface)
    - 객체 생성 메서드는 abstract으로 정의하여, 서브 클래스(4)에서 생성 방식을 결정하도록 함. → Creator class는 생성에 대한 직접적인 책임을 갖고있지 않음.
4. ConcreteCreator
    - 객체 생성 방식, 타입을 결정하는 클래스

→ 객체 생성 로직을 분리하는 패턴이기 때문에, 새로운 객체(concrete product)를 추가하기 쉽다.

## 예제

- User interface

```java
public interface User{
	void signup();
}
```

- User의 구현체(NaverUser, KakaoUser)

```java
public class NaverUser implements User{
	@Override
	public void signup(){
		System.out.println("Naver signup");
	}
}

public class KakaoUser implements User{
	@Override
	public void signup(){
		System.out.println("Kakao signup");
	}
}
```

- User를 생성하는 creator

```java
public abstract class UserCreator{
	public User newInstance(){
		User user = createUser();
		user.signup();
		return user;
	}
	protected abstract User createUser();
}
```

- creator의 구현체들

```java
public class NaverUserCreator extends UserCreator{
	@Override
	protected User createUser(){
		return new NaverUser();
	}
}

public class KakaoUserCreator extends UserCreator{
	@Override
	protected User createUser(){
		return new KakaoUser();
	}
}
```

- client

```java
//client
//naver creator
UserCreator userCreator = new NaverUserCreator();
User newUser = userCreator.newInstance();
```

- 새로운 User 객체를 추가하는 경우

```java
public class GoogleUser implements User{
	@Override
	public void signup(){
		System.out.println("Google signup");	
	}
}
```

→ 기존 코드에 대한 수정 없이 새로운 클래스의 추가만으로도 확장이 가능하다!!(OCP-Open&Closed)

### Q.

- abstract factory method pattern과의 차이점

### Reference

[https://refactoring.guru/design-patterns/factory-method](https://refactoring.guru/design-patterns/factory-method)

[https://bcp0109.tistory.com/367](https://bcp0109.tistory.com/367)
