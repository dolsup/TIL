# 도메인 주도 설계

> 에릭에반스, 이대엽 역, 위키북스, 2011 [링크](http://www.yes24.com/24/Goods/5312881?Acode=101)



# 1부 동작하는 도메인 모델 만들기

- 모든 소프트웨어는 그 소프트웨어를 사용하는 사용자 활동이나 관심사와 관련돼 있음. 사용자가 프로그램을 사용하는 대상 영역이 바로 해당 소프트웨어의 도메인(Domain)임.
- 소프트웨어의 본질은 해당 소프트웨어 사용자를 위해 도메인에 관련된 문제를 해결하는 능력에 있음.
- 따라서 개발팀은 사용자 활동과 관련된 지식 체계에 집중해야 하는데 이 지식의 폭은 위압적일 수 있음. 모델은 **지식을 선택적으로 단순화하고 의식적으로 구조화** 한 형태.

##### 도메인 주도 설계에서 모델의 유용성
1. 모델과 핵심 설계는 서로 영향을 주며 구체화 됨.
2. 모델은 모든 팀 구성원이 사용하는 언어의 중추.
3. 모델은 지식의 정수만을 뽑아낸 것.

## 1장 지식탐구
지식탐구는 팀 내 지식을 가치 있는 모델로 만듬.
- 엄청난 양의 정보 속에서 아주 미미한 관련성을 찾음. 전체를 이해할 수 있는 간결한 관점을 찾아 체계적인 아이디어들을 차례로 시도. 그 과정에서 수 많은 모델이 시도, 거부, 변형 됨.
- 지식 탐구는 혼자서 하는 활동이 아님. 개발자와 도메인 전문가로 구성된 팀은 대체로 개발자가 이끄는 가운데 협업함.
- 도메인 모델의 지속적인 정제를 토대로 개발자는 기능만을 기계적으로 만드는데 머무르지 않고 자신이 보조하고 있는 업무의 중요 원칙들을 배움.
- 모델은 결코 완벽해질 수 없음. 다만 계속 발전해 나갈 뿐.

## 2장 의사소통과 언어 사용
도메인 모델은 소프트웨어 프로젝트를 위한 공통 언어의 핵심이 될 수 있음. 프로젝트에서 언어를 사용하는 것은 미묘하지만 아주 중요.

- 도메인 전문가는 자신의 전문 용어를 사용하고 개발팀은 설계 측면에서 도메인에 관한 토론에 적합한 자신들만의 언어를 사용
- 일상적인 토론에서 쓰이는 용어가 코드에 녹아든 용어와 단절

이런 일은 발생하면 번역이 필요하게 되고 번역은 의사소통을 무디게 하고 지식 탐구를 빈약하게 만듬.

> 위에서 언급 된 번역의 문제 말고, 영어 - 한국어 간의 번역 문제는 어떨까. 코드는 영어로 작성 되는데 도메인 전문가와의 토론에는 한국어를 사용해야 한다. 즉, 코드 상에서 모델들은 전부 영어로 번역되야 하는데 이 과정에서 발생하는 문제는?

##### 유니쿼터스 언어(Ubiquitous Language)를 구성하는 어휘
- 클래스와 주요 연산의 이름
- 모델 내 명시적으로 드러나는 규칙을 토론하기 위한 용어
- 모델에 부과된 높은 수준의 구성 원칙에서 비롯된 용어
- 팀에서 일반적으로 도메인 모델에 적용하는 패턴의 이름

모델 기반 언어는 개발자 사이에서 시스템 산출물 뿐 아니라 업무와 기능을 기술할 때도 사용해야 함. 아울러 이 모델은 개발자 - 도메인 전문가가 서로 의사소통하는 것 뿐 아니라 도메인 전문가들끼리 소통하는데도 언어를 제공해야 함. **언어의 변화는 도메인 모델의 변화로 인식**되어야 한다.

## 3장 모델과 구현의 연계
도메인 주도 설계에서는 초기 분석 단계에 도움될 뿐 아니라 설계의 기반이 되는 모델이 필요. 코드와 그것의 기반이 되는 모델이 긴밀하게 연결되면 코드에 의미가 부여되고 모델과 코드가 서로 대응하게 됨.
순수하게 이론에만 치우친 분석 모델(analysis model)은 심지어 도메인의 이해라는 가장 주된 목표에 미치지 못하기도 하는데, 중요한 발견은 언제나 설계/구현을 위해 노력하는 가운데 나타나기 때문. 설계 혹은 설계의 주된 부분이 도메인 모델과 대응하지 않는다면 그 모델은 가치가 없음.

> 객체 설계에서의 진정한 도약은 코드가 모델의 개념을 표현할 때 나온다.



# 2부 모델 주도 설계의 기본 요소

## 4장 도메인의 격리

도메인에 관련된 코드가 상당한 양의 도메인과 관련 없는 다른 코드가 섞여 있을 때, 도메인에 관련된 코드를 확인하고 추론하기가 굉장히 힘들어짐. 예를 들어 UI를 표면적으로 변경하는 것이 실질적으로 업무 로직을 변경하는 것으로 이어질 수 있음.

![layered-archicture](https://www.citerus.se/wp-content/uploads/2009/09/dddlayers.png)

소프트웨어 프로그램은 갖가지 작업을 수행하는 설계와 코드가 포함됨. 이를 분리하는 방법은 다양하지만 LAYERED ARCHITECTURE가 널리 받아들여지고 있음. 
- 한 계층의 모든 요소는 오직 같은 계층에 존재하는 다른 요소나 계층상 "아래"에 위치한 요소에만 의존. 즉, 한 방향으로만 느슨하게 결합됨.
- 각 계층에서 컴퓨터 프로그램의 특정 측면만을 전문적으로 다룸. 이로써 각 측면에서 더욱 응집력 있는 설계가 가능하고, 설계를 이해하기 쉬워짐.

> 도메인계층 (또는 모델 계층): 업무 개념과 업무 상황에 관한 정보, 업무 규칙을 표현하는 일을 책이짐. 이 계층에서는 업무 상황을 반영하는 상태를 제어하고 사용하며, 그와 같은 상태 저장과 관련된 기술적인 세부사항은 인프라스트럭처에 위임. 이 계층이 업무용 소프트웨어의 핵심.

도메인 모델과 관련 된 코드를 모두 한 계층에 모으고 사용자 인터페이스, 애플리케이션 코드, 인프라스트럭처 코드와 격리함으로써 도메인 모델을 표현하는 것에만 집중할 수 있음. 이로써 모델은 진화를 거듭해 본질적인 업무 지식을 포착해서 풍부하고 명확해질 것임.

## 5장 소프트웨어에서 표현되는 모델

##### 모델을 표현하는 세 가지 패턴
- 연속성과 식별성을 지닌 것을 의미하는가? Entity
- 다른 뭔가의 상태를 기술하는 속성에 불가한가? Value Object
- 객체보다는 행동(action)이나 연산(operation)으로 좀 더 명확하게 표현되는가? Service

모델링과 실제 구현 간의 상호작용은 여러 객체 간의 연관관계에서 특히 까다로움. 연관관계를 좀 더 쉽게 다루기 위해서는 가능한 한 관계를 제약하는 것이 중요함.
- 탐색 방향을 부여
- 한정자(qualifier)를 추가해서 사실상 다중성(multiplicity)을 줄임
- 중요하지 않은 연관관계를 제거

### Entity
엔티티의 가장 기본적인 책임은 객체의 행위가 명확하고 예측 가능해질 수 있게 연속성을 확립하는 것. 자신의 생명주기동안 형태와 내용이 급격하게 변할 수 있지만 연속성은 유지해야 함. 엔티티를 모델링할 때는 개념에 필수적인 **행위**만 추가하고 그 행위에 필요한 속성만 추가.

##### 식별 연산의 설계
자바의 `==` 연산은 두 객체의 메모리 주소나 다른 어떤 메커니즘을 기준으로 두 객체 참조가 같은 객체를 가리키고 있는지 판단함.
하지만 이 같은 식별 메커니즘은 도메인에서는 의미하는 바가 크지 않음.

- 모델이 동일하다는 것이 무슨 의미인지 정의해야 함.
- 식별성에 대한 정의는 모델로부터 나옴. 따라서 식별성을 정의하려면 도메인을 이해해야 함.
- ID의 유일성이 컴퓨터 시스템의 범위를 넘어 적용돼야 하는 경우도 있음.


### Value Object
사물을 서술하는 객체. 개념적 식별성을 갖지 않으면서 도메인 서술적 측면을 나타냄. 값 객체는 설계 요소를 표현할 목적으로 인스턴스화 됨. 우리는 이러한 설계 요소가 어느 것인지에 대해서는 관심 없음. 오직 해당 요소가 무엇인가에 대해 관심.

- 모델에 표함된 어떤 요소가 속성에만 관심이 있다면 그것을 값 객체로 분류할 것. 
- 값 객체는 불변적(immutable)로 다뤄야 함. 
- 아무런 식별성도 부여하지 말고 엔티티를 유지하는데 필요한 설계상의 복잡성을 피해야 함.
- 구성하는 속성은 개념적 완전성(conceptual whole)을 형성해야 함.

동일한 값 객체가 두 객체 간에 공유될 수 있는데(동일한 인스턴스를 가르키는 포인터를 보유하는 식으로) 이 때, 한 쪽에서 값이 변경 되면 기대한대로 동작하지 않을 수 있음. 따라서 객체를 안전하게 공유할 수 있으려면 해당 객체가 불변적이어야 함.

### Service
- 개념적으로 어떠한 객체에도 속하지 않는 연산. 
- 사물이 아닌 활동(activity)이나 행동(action).
- 도메인의 개념 가운데 객체로는 모델에 어울리지 않는 것.

연산의 명칭은 보편언어(Ubiquitous Language)에서 유래하거나 보편언어에 도입돼야 함. 또한 서비스의 매개변수와 결과는 도메인 객체여야 함. 잘 만들어진 서비스는 다음 특징을 가짐.

- 연산이 원래부터 엔티티나 값 객체의 일부를 구성하는 것이 아니라 도메인 개념과 관련.
- 인터페이스가 도메인 모델의 외적 요소의 측면에서 정의 됨.
- 연산이 상태를 갖지 않음.

### Module (또는 Package)
모듈화의 가장 주된 이유는 바로 인지적 과부화 때문임. 모듈로 쪼개지는 것은 코드가 아닌 바로 **개념**임. 어떤 클래스들을 한 모듈안에 함께 둔다면 그것은 바로 옆에서 설계를 살펴보는 동료 개발자에게 그 클래스들을 하나로 묶어서 생각하자고 말하는 것과 같다.

모델과 마찬가지로 모듈도 계속 발전해야 하지만 대게 그렇게 되지 않음. 이유는
- 초기에는 모듈이 객체의 형태를 조직화할 목적으로 사용 됨.
- 그 후 객체는 기존 모듈이 정의한 범위 안에 머무룰 수 있는 방식으로 변화함.
- 모듈을 리팩터링하는 것은 클래스를 리팩터링 하는 것보다 더 일이 많고 파급효과가 큼.

그러나 모델 객체가 원시적이고 구체적인 상태에서 점차 변형되어 더욱 심층적인 통찰력을 드러내는 것처럼 모듈도 정교해지고 추상적인 형태로 변화할 수 있음.

### 모델링 패러다임 (TODO: 나중에 다시 보기)
MODEL-DRIVEN DESIGN은 현재 적용중인 특정 모델링 패러다임과 조화를 이루는 구현 기술을 필요로 함. 현재는 객체지향 설계가 가장 지배적임. 
- 대부분의 사람들이 객체지향 개념을 자연스럽게 이해.
- 객체 모델링의 개념은 단순하지만 중요한 도메인 지식을 포착할 만큼 풍부함.
- 패러다임의 성숙과 함께 널리 보급됨.
- 개발자 커뮤니티와 설계 문화 자체도 성숙 됨.

현재로써 MODEL-DRIVEN DESIGN을 시도하는 대다수 프로젝트에서는 시스템 기반에 객체지향 기술을 사용하는 것이 현명함. 하지만 언제나 정답은 아님.

# 3부 더 심층적인 통찰력을 향한 리팩터링
## 10장 유연한 설계
### 의도를 드러내는 인터페이스
- 명확히 표현 된 규칙 없이 암묵적인 규칙에 따라 실행되는 코드를 이해하려면 소프트웨어 프로시저를 구성하는 각 단계를 기억해야 함. 또한, 모델과의 연관관계가 분명하지 않을 경우 코드의 수행 결과를 이해하거나 변경의 파급 효과를 예상하기 어려움.
- 객체가 아름다운 이유는 이 모든 것을 캡슐화할 수 있기 때문. 캡슐화로 클라이언트 코드는 단순해지고 상위 수준에서 코드를 이해. 반면 객체를 사용하는데 알아야 할 정보를 인터페이스로부터 얻지 못한다면 세부적인 측면을 이해하고자 객체 내부를 깊이 파고들 수 밖에 없음. 이 순간 캡슐화의 가치를 잃어버림.
- 클래스와 연산을 추가하기 전에 행위에 대한 테스트를 먼저 작성. 객체에게 이야기하고 싶은 방식을 반영하는 테스트를 작성.
- 클래스와 연산의 이름은 수행 방법에 관해 언급하지 말고 결과와 목적만을 표현해야 함.
- 방법이 아닌 의도를 표현하는 추상적인 인터페이스 뒤로 모든 까다로운 메커니즘을 캡슐화.

### 부수효과가 없는 함수
- 연산은 크게 명령과 질의로 나뉨. 명령은 부수효과를 일으킴.
- 명령과 질의를 엄격하게 분리된 연산으로 유지하고 변경을 발생시키는 행위는 도메인 데이터를 반환하지 않고 가능한 단순한 연산으로 엄격하게 분리. 
	- 도메인 데이터를 반환하면 메서드 바깥쪽에서 잘못 참조하거나 또 다른 변화를 일으킬까봐 그런 듯함.
- 책임에 적합한 어떤 개념이 나타난다면 복잡한 로직을 값 객체로 옮겨 부수효과를 통제. 값 객체는 불변 객체이며 생성할 때 호출되는 초기화 연산을 제외하면 모든 연산이 함수임.

### 단언
- 연산의 사후조건과 클래스 및 Aggregate의 불변식을 자동화된 단위 테스트, 또는 적절한 문서나 다이어그램으로 Assertion을 서술.
- 다른 개발자들이 의도된 Assertion을 추측할 수 있게 인도하고, 쉽게 배울 수 있고 모순 된 코드를 작성하는 위험을 줄이는 응집도 높은 개념이 포함 된 모델을 만드려고 노력.

### 개념적 윤곽
- 높은 응집도, 낮은 결합도. 두 원리는 개별 메서드부터 클래스와 모듈 그리고 대규모 구조 뿐만 아니라 개념에 대해서도 중요한 역할.
- 기계적 관점에서 개념을 바라보는 함정을 피하려면 다음과 같은 자문을 해볼 것. “이 개념이 현재 모델과 코드에 포함된 관계를 기준으로 했을 때 적절한가, 또는 현재 기반을 이루는 도메인과 유사한 윤곽을 나타내는가?”
- 개념적으로 의미 있는 기능의 단위를 찾게 되면 그 결과로 만들어진 설계는 유연하고 이해하기 쉬워짐.
- 새로 알게 된 개념이나 요구사항을 코드에 적용하며 반복적인 리팩터링을 토대로 변하는 부분과 변하지 않는 부분을 나누는 중심 축을 식별.
- 목표는 유비쿼터스 언어를 사용해 단순한 인터페이스 집합을 얻는 것. 이는 일반적으로 리팩터링을 통해 달성할 수 있으며, 사전 설계로 달성하기는 어려움 (사전 설계 때 모든 도메인 지식을 완전히 얻기 어렵기 때문인 듯). 여기서 말하는 리팩터링은 기술 지향적 리팩터링을 의미하는 것이 아님.

### 독립형 클래스
- TODO: 나중에 다시 읽기. 잘 이해 안 됨.
- 의존성이 하나만 있더라도 동시에 두 개의 클래스를 고려 해야 함. 두 개의 의존성이 존재한다면 세 개의 클래스를, 의존성이 세 개라면… 고려할 사항은 눈덩이처럼 불어남.
- MODULE 과 AGGREGATE 로 묶더라도 의존성이 증가할수록 설계를 파악하는데 따르는 어려움이 가파르게 높아지는건 변함 없음. 이는 개발자에게 정신적 과부화를 줌.
- 객체 개념을 구성하는데 필수적이라는 사실이 증명되기 전까지는 모든 의존성을 검토해야 함. 이러한 과정은 모델 개념 자체를 분해하는 것에서 출발. 그런 다음 개별 연관관계와 연산에 주목.

### 연산의 닫힘
- TODO: 잘 안읽힘. 나중에 다시 읽기.
