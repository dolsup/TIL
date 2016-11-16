# 개발자가 반드시 정복해야 할 객체지향과 디자인패턴

> [객체 지향과 디자인 패턴 | 저자 최범균|인투북스 |2013.07.05](http://book.naver.com/bookdb/book_detail.nhn?bid=7255217)

위 책 중 객체지향과 관련 된 부분만 정리한다. 추후 이 책을 통해 다시 학습할 내용은

- SOLID 설계 원칙
- 디자인 패턴



## 객체지향

객체지향은 데이터 및 데이터와 관련된 프로시저를 객체(object)라고 불리는 단위로 묶는다.

- 프로그램의 규모가 작을 때, 절차지향방식보다 더 복잡한 구조를 갖게 된다. 하지만 요구사항의 변화가 발생했을 때 절차 지향 방식보다 프로그램을 더 쉽게 변경할 수 있는 장점을 갖는다.(p.33)

### 객체의 핵심은 기능을 제공하는 것

객체를 정의할 때 사용되는 것은 객체가 제공해야 할 기능이며, 객체가 내부적으로 어떤 데이터를 갖고 있는 지로는 정의되지 않는다. (중략) 기능을 제공한다는 것이 중요할 뿐이다.(p.33)

이는 다시 말하면 객체마다 자신만의 책임(responsibility)이 있다는 의미를 갖는다. (중략) 그럼 객체가 갖는 책임은 어떻게 결정될까? 이 결정을 하는 것이 바로 객체 지향 설계의 출발점이다.(p.37) 

### 의존

객체를 생성하든 메서드를 호출하든 또는 파라미터로 전달받든 다른 타입에 의존을 한다는 것은 의존하는 타입에 변경이 발생할 때 나도 함께 변경될 가능성이 높다는 것을 뜻한다.(중략) 의존의 영향은 꼬리에 꼬리를 문 것처럼 전파되는 특징을 갖는다. 예를 들어, C클래스가 B클래스에 의존하고, B클래스가 A클래스에 의존한다고 하자. 이 경우, A클래스의 변경은 B클래스에 영향(변경)을 줄 가능성이 높고, 이는 다시 C클래스에 영향을 주게 된다.(p.42)

- 내가 변경되면 나에게 의존하고 있는 코드에 영향을 준다.
- 나의 요구가 변경되면 내가 의존하고 있는 타입에 영향을 준다.

### 캡슐화

객체지향의 장점은 한 곳의 구현 변경이 다른 곳에 변경을 가하지 않도록 해준다는데 있다. 즉, 수정을 좀 더 원할하게 할 수 있도록 하는 것이 객체지향적으로 프로그래밍을 하는 이유인 것이다. (중략) 캡슐화(encapsulation)는 객체가 내부적으로 기능을 어떻게 구현하는지를 감추는 것이다. 이를 통해 내부의 구현이 변경되더라도 그 기능을 사용하는 코드는 영향을 받지 않도록 만들어 준다. 즉, 내부 구현 변경의 유연함을 주는 기법이 바로 캡슐화이다.(p.45) 

- Tell, Don't Ask
- 데미테르의 법칙

### 객체지향설계과정

1. 제공해야 할 기능을 찾고 또는 세분화하고, 그 기능을 알맞은 객체에 할당한다.
   - 기능을 구현하는데 필요한 데이터를 객체에 추가한다.
   - 기능을 최대한 캡슐화해서 구현한다.
2. 객체 간에 어떻게 메시지를 주고받을지 결정한다.
3. 과정1과 과정2를 개발하는 동안 지속적으로 반복한다.(p.55)

### 다형성

다형성(Polymorphism)은 한 객체가 여러가지(poly) 모습(morph)을 갖는다는 것을 의미한다. 여기서 모습이란 타입을 뜻하는데, 즉, 다형성이란 한 객체가 여러 타입을 가질 수 있다는 것을 뜻한다.(p.62)

### 추상타입

추상화(abstraction)는 데이터나 프로세스 등을 의미가 비슷한 개념이나 표현으로 정의하는 과정이다.(p.66)

### 상속

상속을 사용하면 쉽게 다른 클래스의 기능을 재사용하면서 추가 기능을 확장할 수 있기 때문에, 상속은 기능을 재사용하는 매력적인 방법이다. 하지만, 상속은 변경의 유연함이라는 측면에서 치명적인 단점을 갖는다.(p.88)

- 상위 클래스 변경의 어려움: 상속 계층을 따라 상위 클래스의 변경이 하위 클래스에 영향을 주기 때문에, 최악의 경우 상위 클래스의 변화가 모든 하위 클래스에 영향을 줄 수 있다.
- 클래스의 불필요한 증가
- 상속의 오용(IS-A를 만족하지 않는 상속관계 구현 등)

상속을 사용할 때에는, 재사용이라는 관점이 아닌 기능의 확장이라는 관점에서 상속을 적용해야 한다. 또한 추가로 명확한 IS-A 관계가 성립되어야 한다. 대표적인 예가 UI위젯이다.(p.101)



## 객체지향설계원칙 SOLID

### 단일책임원칙(Single responsibility principle)

- 클래스는 단 한개의 책임을 가져야 한다.

클래스가 여러 책임을 갖게 되면 그 클래스는 각 책임마다 변경 되는 이유가 발생하기 때문에, 클래스가 한 개의 이유로만 변경되려면 클래스는 한 개의 책임만을 가져야 한다. 다른 말로 "클래스를 변경하는 이유는 단 한 개여야 한다"고도 표현한다.(p.105)

### 개방폐쇄원칙(Open-closed principle)

- 확장에는 열려 있어야 하고, 변경에는 닫혀 있어야 한다.

이 말을 구체적으로 풀어 보면 기능을 변경하거나 확장할 수 있으면서, 그 기능을 사용하는 코드는 수정하지 않는다.(p.111)

### 리스코프치환원칙(Liskov substitutino principle)

리스코프 치환원칙은 개방 폐쇄 원칙을 받쳐주는 다형성에 관한 원칙을 제공한다.

- 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.

리스코프 치환 원칙은 계약과 확장에 관한 것(p.122)

### 인터페이스분리원칙(Interface segregation principle)

- 인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리되어야 한다. (원래의 정의는 클라이언트는 자신이 사용하는 메서드에만 의존해야 한다)

각 클라이언트가 사용하는 기능을 중심으로 인터페이스를 분리함으로써, 클라이언트로부터 발생하는 인터페이스 변경의 여파가 다른 클라이언트에 미치는 영향을 최소화 할 수 있게 된다. (p.129)

### 의존역전원칙(Dependency inversion principle)

- 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다. 저수준 모듈이 고수준 모듈에서 정의한 추상 타입에 의존해야 한다.

의존 역전 원칙은 소스 코드에서 의존을 역전시키는 원칙이다. (중략) 런타임이 아닌 소스 코드의 의존을 역전시킴으로써 변경의 유연함을 확보할 수 있도록 만들어 주는 원칙이지, 런타임에서의 의존을 역전시키는 것은 아니다.(p.133)