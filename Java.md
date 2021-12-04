#### [1. interface 및 abstract](#1-interface-abstract)

# 1 interface abstract
### interface 와 abstract는 객체지향 원칙중에서 추상화와 다형성에 해당하는 부분이다.
### Java기준에서 interface는 implement로, abstract는 extends로 SubClass에서 상속 받아서 사용한다.

### 예를 들어 Animal 이라는 abstract, interface 클래스를 만들어서 개와 고양이 Class를 구현해 보겠다.

```java
--------------------------abstract--------------------------
abstract class Animal{
    abstract void sound();
    public void leg(){
        System.out.println("다리는 4개 입니다");
    }
}

class Cat extends Animal{
    @Override
    public void sound() {
    	System.out.println("야옹");
    }
}

class Dog extends Animal{
    @Override
    public void sound() {
    	System.out.println("멍멍");
    }
}

public class codeTest {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Animal dog = new Dog(); 
		dog.sound();
		dog.leg();
		
		Animal cat = new Cat();
		cat.sound();
		cat.leg();
	}
}

실행결과:
멍멍
다리는 4개 입니다
야옹
다리는 4개 입니다


--------------------------interface--------------------------
interface  Animal{
    void sound();
    void leg();
}

class Cat implements Animal{
    @Override
    public void sound() {
       	System.out.println("야옹");
    }
    @Override
    public void leg() {
       	System.out.println("다리는 4개 입니다");
    }
}

class Dog implements Animal{
    @Override
    public void sound() {
    	System.out.println("멍멍");
    }
    @Override
    public void leg() {
       	System.out.println("다리는 4개 입니다");
    }
}

public class codeTest {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Animal dog = new Dog(); 
		dog.sound();
		dog.leg();
		
		Animal cat = new Cat();
		cat.sound();
		cat.leg();
	}
}

실행결과:
멍멍
다리는 4개 입니다
야옹
다리는 4개 입니다
```
### abstract의 특징은 공통 부분은 일반 메소드를 포함하여 상속 받아 일반 메서드를 사용 할 수 있다. extends의 단어의 뜻은 연장하다 이다 그 뜻은 부모 클래스가 하던일을 여러명의 자식들이 필요한 메서드에 한애서 상속 받아 재정의 하기 위한 역할이라고 생각한다.

<br>   

### interface의 경우 내부에 일반 메소드를 정의 할 수 없고 모든 메서드를 연장해서 재정의 해줘야한다. implements의 단어의 뜻은 도구, 시행하다 인데 implement는 구현하다 라는 뜻을 가지고 있다. 모든 메서드를 자식 클래스에서 재정의 해줘야 오류가 안나고 사용 가능하다.
<br>

### ※ 차이점은 abstract의 경우 부모가 낳아주고 길러주다가 부모의 직업을 이어받아 필요한 부분은 나만의 스타일로 꾸민다.
### interface의 경우 부모가 낳아주고 길러주어 직종을 이어 받아 나만의 스타일로 모든 부분을 꾸미는 느낌 이라고 생각한다. 
<br>

### 또한 Java의 경우 다중상속을 지원하지 않는다 예를 들어
```java
class Cat extends Animal, etc.. {
}
이러한 경우 오류가 발생한다

class Cat implements Animal, etc.. {
}
etc..가 다른 interface라면 여러개의 클래스를 재정의 해줄 수 있는 차이점이 있다
```
