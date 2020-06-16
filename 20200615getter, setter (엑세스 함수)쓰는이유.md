# getter, setter (엑세스함수)쓰는이유

```java
class Human{
	int age;
	String name;
	
	private void setAge(int age){
		if (age < 0){
			return raise errer;
		}
		this.age = age;
		return true;
	}
}
```

캡슐화를 해야하는 이유.

- 정환

- <h4>한 오브젝트의 내부속성을 외부에서 알지 못하게 하고, 접근이 불가능하게 하여 객체지향의 목적인 `정보은닉` 과 `객체의 무결성 보장`을 위함 + validation을 하기 위해서<h4/>

- getter의 경우 해당 프로퍼티를 복사해서 반환하기 때문에 무결성을 지켜줄 수 있는 방법이 된다.

- 또한 변화에 유연하게 대처할 수 있는 방법이 됨 / 추가설명 출처: http://egloos.zum.com/invers83/v/4113861

- 하지만 한 단계 더 깊이 생각해보면  액세스 함수(getter setter)를 최대한 사용하지 말라는 얘기가 있다. 엑세스 함수를 남발하는것은 오히려 무결성을 헤칠 수 있다는 의견인데,  무결성을 엄밀히 지키려면, **생성 이후에는 객체 내부의 데이터를 조작할 수 있는 단하나의 방법은 공개된 메소드를 통한 조작으로만 가능해야하지 엑서스 함수로 조작이 되서는 안된다.** 

- 이 말을 이해하기 위해서는 getter 동작방식을 이해해야 하는데, 윈시데이터를 접근할때는 원본데이터를 복사해서 반환하지만, 오브젝트필드를 getter로 접근할때는 레퍼런스 값을 반환하기 때문에 **필드 객체에 접근하면서 이를 조작할 수도 있다.**

- 이러한 접근은 **데미테르 법칙**을 애초에 위반하는 방법이기도 하지만, 이 법칙을 강제적으로 사용하지 못하도록 엑서스 함수를 선언하지 않으면 된다는 의견이 있다.

- 예를들어, 사람 객체에 주소객체가 있다고 하자.

```java
class Person{
	private Address address;
	private String name;
	public Person(Address address, String name){
		this.address = address;
		this.name = name;
	}
	// 주소게터 주소세터 이름 게터 이름세터 있다고 보자
}
class Address{
	private String zipcode;
	private String doSiGuGun;
	public Address(String zipcode, String doSiGuGun){
		this.zipcode = zipcode;
		this.doSiGuGun = doSiGuGun;
	}
	public String getZipcode(){
		return this.zipcode;
	}
	public void setZipcode(String newZipcode){
		this.zipcode = newZipcode;
	}
	
}

// 로직

Person p = new Person(new Address("123456", "주소주소"), "이신호");

p.getAddress().setZipcode("654321");
// 가능!!
// 하지만 이런식으로 접근하여 바꿀 수 있다는 것 자체가 우리가 의도한 메소드라기 보다는 그냥 엑세스 함수로서 존재할때 이러한 동작이 가능하다는 것이다. 엄밀히 설계하려면 이런식의 접근 자체를 방지해야 한다.

```





- 자세한사항은 뒤에 캡슐화에서 보자.