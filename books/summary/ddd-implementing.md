# 도메인 주도 설계 구현

> 반 버논, 윤창석, 황예진 역, 에이콘출판, 2016 [링크](https://book.naver.com/bookdb/book_detail.nhn?bid=10382647)



에릭에반스의 [도메인 주도 설계](ddd.md) 6장을 읽다가 도무지 무슨 말을 하는 건지 이해가 잘 안되서 반 버논의 DDD를 읽기 시작.



## 1장 DDD를 시작하며

우리는 개발하는 소프트웨어의 품질을 높이려고 많은 노력을 함. 

> 하지만, 버그 없는 소프트웨어 != 양질의 소프트웨어 모델(원하는 비즈니스 목표를 이루도록 솔루션을 제공해 주는 방법) 설계

DDD의 가장 중심에 있는 원리는 (비즈니스 가치를 만들기 위해서, 가치를 만들기 위해 모인 사람이 모두 함께) 토의, 경청, 이해, 발견, 그리고 비즈니스의 가치. 모든 지식을 중앙화 하는 것.



### DDD를 하는 이유

- 도메인 전문가와 개발자의 눈 높이를 맞춘다. 소프트웨어 개발자뿐 아니라 비즈니스 관계자에게도 말이 되는 소프트웨어를 만듬.
  - 우리에겐 도메인 전문가가 없는데? 도메인 전문가는 단순 직책이 아님. 비즈니스 과정을 잘 알고 있는 사람들임. 그들은 비즈니스 도메인에 대한 배경지식을 많이 갖고 있을 뿐 아니라 상품 디자이너거나 영업 인력일 수 있음.
- 비즈니스의 현 상태에 대해 더 알려줄 수 있음. DDD를 통해, 지속적으로 비즈니스를 발견해 나가며 모든 사람이 배우게 됨.
- 도메인 전문가와 소프트웨어 개발자가 공통의 언어를 사용.
- 지식의 중앙화. 프로젝트에 참여한 일부만이 지식을 공유하는 것이 아닌 비즈니스 관련자가 모두 지식을 공유함.

일반적으로 도메인 전문가는 비즈니스의 가치를 제공하는 데, 소프트웨어 개발자는 기술적 해결하는데 집중함. 진정으로 비즈니스 가치를 제공하는 소프트웨어는 전략적 비즈니스 발의와 뜻을 같이하며 기술에 관한 것이 아닌 **비즈니스에 관한 솔루션**을 제공. 나쁜 경우는 소프트웨어가 비즈니스를 잘못된 방향으로 변경할 때 (책에서는 ERP 소프트웨어에 맞춰 조직의 비즈니스 전반을 변경하는 사례를 예로 듬).



### DDD가 해줄 수 있는 일

- 도메인 전문가와 소프트웨어 개발자가 비즈니스 전문가의 심적 모델을 반영한 소프트웨어를 함께 개발할 수 있게 해줌. 절대로 '우리와 그들'을 나누지 않고 항상 '우리'여야 함.
- 비즈니스의 전략적 이니셔티브<sup>initiative</sup> (KPI의 목표 달성을 전략적으로 가능케하는 핵심적인 활동, 계획 또는 구상)를 다룸.
- 실제 소프트웨어의 기술적 요구에 응함. 도메인 전문가의 심적 모델이 코드화 되고, 서비스 수준 계약<sup>SLA</sup>을 수행.



### DDD를 사용하는 데서 오는 비즈니스 가치

어떤 기술이나 기법을 사용할 때의 가장 훌륭한 정당화는 **비즈니스에 가치를 제공**하는 경우임.

- 조직이 그 도메인에 유용한 모델을 얻음.
- 정교하고 정확하게 비즈니스를 정의하고 이해.
- 도메인 전문가가 소프트웨어 설계에 기여.
- 사용자 경험이 개선.
- 순수한 모델 주변에 명확한 경계가 생김.
- 엔터프라이즈 아키텍쳐 구성이 좋아짐 (바운디드 컨텍스트, 컨텍스트 맵 등의 도입으로 인함).
- 애자일하고, 반복적이고, 지속적인 모델링이 사용됨.



### DDD 적용의 난관

- 유비쿼터스 언어를 만드는 데 드는 시간과 노력을 계산하는 것.
- 도메인 전문가를 시작부터 참여시키고 프로젝트 내내 함께하는 것.
- 도메인 내의 해결책에 관한 개발자의 사고방식을 바꾸는 것.



### 유비쿼터스 언어

- 팀 내에 공유된 언어. 도메인 전문가, 개발자, 해당 프로젝트에 참여하는 모든 사람 간에 공유된 언어.
- 반드시 업계 표준 용어를 사용해야 하는건 아님. 함께 공유하기만 하면 됨.
- 언어의 품질에 대해서만큼은 절대 타협하지 않으며, 오직 가장 좋은 개념과 용어의 의미가 무엇인지란 측면에서 타협함.



## 2장 도메인, 서브도메인, 바운디드컨텍스트

### 도메인
- 다소 여러 의미를 가지는 용어.
- 넓은 의미에서 한 조직이 행하는 일과 그 조직 안의 세계.
- 거의 모든 소프트웨어 도메인에는 다수의 서브 도메인이 있음.

### 핵심도메인
- 비즈니스 목표와 맥을 같이하며 서브도메인과 그 안의 모델은 지속적으로 정제되고 확장되어 감.
- 서브도메인은 크게 핵심도메인과 그 외의 도메인 (지원 서브 도메인, 범용 서브 도메인)으로 나눌 수 있음.
- 핵심 도메인은 비즈니스에 분명한 이점을 제공하기 때문에 구현에 탁월함이 요구 됨.

## 전자상거래 시스템 예시
![서브도메인과 바운디드 컨텍스트를 포함한 도메인](https://user-images.githubusercontent.com/13076271/46058907-de623280-c197-11e8-9be3-734184d39f02.png)

- 전자상거래 라는 전체 비즈니스 도메인.
- 논리적으로 상품 카탈로그, 주문, 송장, 배송 네 부분의 주요 서브도메인으로 이뤄짐.
- 반면 물리적으로는 모두 같은 시스템 안에 구성되어 있음. 하나의 시스템이 많은 비즈니스 기능을 책임지고 있음.
- 새로운 기능 추가를 위해 다양한 논리적 모델이 더욱 커져감에 따라, 대립되는 관심사 때문에 진행에 방해를 받음.
- 재고 관리의 경우 오직 하나의 서브 도메인이 있음. 외형적으론 재고 관리 시스템이 전자상거래 시스템보다 DDD적인 상태가 더 낫다고 볼 수 있음. 용어와 의미의 충돌이 적고 통합이 쉬울 가능성이 높기 때문임.



## 3장 컨텍스트맵
// TODO 나중에 다시 읽기



## 4장 아키텍처
// TODO 나중에 다시 읽기



## 5장 엔터티

### 개발자가 도메인 모델 설계 중 흔히 빠지는 함정
- 도메인보다 데이터에 초점을 맞추는 경향이 있음. 데이터베이스에 중점을 두기 때문.
- 도메인 개념 설계시 행동 기반이 아닌 데이터의 속성(열)과 연결(외래 키)을 먼저 생각해버림. 따라서 데이터 모델에 대응하는 객체가 투영.
- 이로 인해 도메인 모델 안에 있는 거의 모든 개념이 Getter/Setter를 너무 많이 갖고 있는 엔티티로 코딩 됨.

### 엔티티를 사용하는 이유
- 도메인 개념의 개별성*individuality*이 필요할 때.
- 엔티티는 고유한 대상으로 긴 시간에 걸쳐 계속해서 변화할 수 있음.
- 변화가 너무 크게 일어나 처음과 많이 달라질 수 있음.
- 하지만 같은 식별자를 가져 식별할 수 있는 객체여야 함.

### 고유 식별자
시간이 흘러도 고유성*uniqueness*의 보존 됨을 보장해줄 수 있는 식별자를 구현하는 법.
- 사용자가 식별자를 직접 제공.
- 애플리케이션이 식별자를 생성.
- 영속성 메커니즘이 식별자를 생성.
- 또 하나의 바운디드 컨텍스트가 식별자를 할당.

### 엔티티의 발견과 내부적인 특성을 찾는 과정
- 도메인 전문가와의 신중한 토론과 요구사항 분석을 통해 발견되지 않은 용어를 찾음.
- 예컨대 이름으로 쓰일 명사, 이를 설명해주는 형용사, 행동을 나타내는 동사.
- 초기엔 용어집과  단순한 사용 시나리오 집합 형태에 맞춰 유비쿼터스 언어를 기록.
- 요구사항을 완전히 다시 정리하고 다른 항목을 추가하고 더 분명하게 다듬으며 실제로 일어나는 일이 무엇인지 정확히 정의함.
- 엔티티를 발견해서 이름을 지은 후에 이를 고유하게 식별하고 찾을 수 있게 해주는 특성/속성을 알아냄.
- 필수 행동을 살펴보고 용어집에 추가함.
- 객체의 역할과 책임을 발견.
- 언어가 코드로 모델링 됨.

### 유효성 검사
- 도메인 객체의 모든 특성/속성이 개별적으로 유효 하다고 객체 전체가 하나의 대상으로 유효한 것은 아님.
- 두 개의 올바른 특성을 조합해 전체 객체가 유효하지 않도록 만들 수도 있음.
- 하나의 객체 전체가 유효 하다고 해서 객체의 컴포지션이 유효 하다고 할 수 없음.
- 따라서 하나 이상의 단계로 이뤄진 유효성 검사를 통해 가능한 모든 문제를 다뤄야 함.

#### 특성/속성의 유효성 검사
- [자가캡슐화](https://martinfowler.com/bliki/SelfEncapsulation.html)를 통해 계약에 의한 설계 접근법 측면에서의 어설션 *asssertion*.
- 모든 데이터로의 액세스가 접근자 메소드를 거쳐가도록 설계함.
```java
public class EmailAddress {
    private String address;

    public EmailAddress(String anAddress) {
        super();
        this.setAddress(anAddress);
    }

    // 세터가 외부에 노출되는 것이 아니라 private access
    private void setAddress(String anAddress) {
    	// 전제조건1. 이메일 주소는 null이 될 수 없다
        if (anAddress == null) { // do something }
	
    	// 전제조건2. 이메일 주소는 빈 문자열이 될 수 없다
        if (anAddress.length() == 0) { // do something }
        
    	// 전제조건3. 이메일 주소는 100자 이내의 길이여야 한다
        if (anAddress.length() > 100) { // do something }

    	// 전제조건4. 이메일 주소는 기본 포맷과 맞아야 한다
        if (!java.util.regex.Pattern.*matches*(
                "\\w+([-+.']\\w+)*@\\w+([-.]\\w+)*\\.\\w+([-.]\\w+)*",
                anAddress)) { // do something }

        this.address = anAddress;
    }
}
```

#### 전체 객체의 유효성 검사
- 전체 객체에 검사에 유용한 방법은 지연 유효성 검사 *Deferred Validation*
- 전체 객체 유효성 검사를 엔티티 내부에 집어넣으면 너무 많은 책임이 부여 되기도 하고 많은 경우 도메인 객체의 유효성 검사는 도메인 객체 자체보다 더 자주 변경 됨.
- 유효성 검사 클래스는 명세 패턴이나 전략 패턴을 구현할 수 있음.
- 유효성 검사 프로세스에서 첫번째 문제가 발생했을 때 예외를 던지는 것보단, 전체 결과를 수집하는 편이 중요.
```java
public class Warble extends Entity {
    @Override
    public void validate(ValidationNotificationHandler aHandler) {
        (new WarbleValidator(this, aHandler)).validate();
    }
}
```
- 책의 예제는 유효성 검사가 필요한 모든 엔티티에 `validate()` 메소드를 위치시키고 계층 슈퍼 타입을 활용.
- 상속보다는 `Verifiable` 같은 인터페이스를 구현하는게 낫지 않을까.. 라고 생각함. 

#### 객체 컴포지션의 유효성 검사
- 개별 엔티티 유효성 뿐만 아니라 하나 이상의 애그리게잇 인스턴스를 포함한 클러스터나 엔티티의 컴포지션의 유효성을 모두 검사.
- 구체적 `Validator` 서브클래스를 필요한 수만큼 인스턴스화 하거나 도메인 서비스를 사용.

### 변화 추적
- 가장 정확하고 실용적인 변경 추적은 도메인 이벤트와 이벤트 저장소를 통해 이뤄짐.
- 애그리게잇에서 실행되며 상태를 바꾸는 모든 중요한 커맨드 마다 고유 이벤트 타입을 생성, 이벤트 이름과 해당 속성을 조합해 명시적으로 변경을 기록할 수 있음.
- 보통 이벤트 소싱 이란 이름의 패턴을 사용함.



## 6장 값 객체

값 객체는 생성과 테스트, 사용, 최적화, 유지 관리가 더 쉽게 해줌.

### 값으로 모델링 되는 객체의 예
- 3, 10, 293.51 같은 숫자
- ‘헬로, 월드!’와 ‘도메인 주도 설계’ 같은 텍스트 문자열
- 날짜와 시각
- 성/이름
- 환율과 색깔
- 우편주소
- 등등

### 값의 특징
#### 1. 측정, 수량화, 설명
- 도메인 내의 어떤 대상을 측정하고 수량화하고 설명하는 개념.
- 예를 들어 사람에겐 나이가 있음. 실재하는 어떤 대상은 아니지만 살아온 햇수를 측정하거나 수량화 함.

#### 2. 불변성
- 값인 객체는 일단 생성되면 변경할 수 없음.
- 값이란 단순히 필요에 따라 오가며, 손상을 일으키지 않고 해롭지도 않은 대상 이어야 함.

#### 3. 개념적 전체
- 값 객체는 하나 이상의 개별적 특성을 가질 수 있고, 각 특성은 서로 연관 됨.
- 여러 특성이 설명하는 바를 모아 전체를 나타냄.
- 특성을 개별적으로 사용한다면 응집력 있는 의미를 제공하지 못하고 있는 것.
- 값 클래스의 생성자는 개념적 전체의 효과성에 영향을 미침. 최종 상태가 한 번에 원자적으로 초기화되도록 보장해야 함.

#### 4. 대체성
- 값 객체가 올바르지 않은 상황이 왔을 때, 현재의 전체를 새로운 값으로  완전히 대체 가능해야 함.

#### 5. 값 등가성
- 두 객체의 타입과 특성을 비교해서 등가성을 결정.
- 타입과 특성이 모두 같다면 해당 값을 등가로 간주.
- 등가 관계의 값 인스턴스가 둘 이상 있다면 둘 중 무엇이든 해당 타입의 엔티티에 속성으로 할당될 수 있음.

#### 6. 부작용이 없는 행동
- 불변성 값 객체의 메소드는 반드시 부작용 없는 함수이여야 함.
- 값을 변경하는 메소드를 구현해야 한다면 자신의 값을 직접 변경하지 않고 자신을 대체하는 새로운 값 인스턴스를 만들어 반환하도록 해야 함.
- 부작용 없는 함수의 이름도 중요함. 예를 들어 `getValuePercentage()`의 사용은 기술적 측면에서의 컴퓨터 명령이지만, `valuePercentage()`는 사람이 유창하게 읽을 수 있는 표현임.

### 값 객체의 테스트
- 모델을 설계하며 필수적인 개념을 포착하기 위해선 클라이언트 관점을 가정해보는 과정이 필수.
- 그렇지 않으면 비즈니스 관점이 아닌 우리만의 관점에서 모델링하는 실수를 할 수 있음.
- 테스트는 반드시 도메인적 의미가 있어야 함.



## 7장 서비스

도메인 내에서 서비스란 도메인 고유의 작업을 수행하는 무상태의 오퍼레이션.

### 도메인 서비스가 아닌 것
- 원격 클라이언트로 하여금 복잡한 비즈니스 시스템과 상효 교류하도록 해주는 큰 단위의 컴포넌트
- 애플리케이션 서비스

### 도메인 서비스를 사용할 수 있는 경우
- 중요한 비즈니스 프로세서를 수행할 때
- 어떤 컴포지션에서 다른 컴포지션으로 도메인 객체를 변형할 때
- 하나 이상의 도메인 객체에서 필요로 하는 입력 값을 계산할 때


```java
// 도메인 시나리오
// 시스템의 사용자는 반드시 인증돼야 하지만, 테넌트가 활성화된 경우에만 인증이 가능하다.

// 클라이언트는
// 1) 테넌트가 활성화 됐는지 확인하고
// 2) 유저를 찾아서 인증 가능여부를 확인

boolean authentic = false;

Tenant tenant = DomainRegistry
        .tenantRepository()
        .tenantOfId(aTenantId);

if (tenant != null && tenant.isActive()) {
    User user = DomainRegistry
            .userRepository()
            .userWithUserName(aTanantId, aUsername);

    if (user != null) {
        authentic = user.isAuthentic(aPassword);
    }
}

return authentic;

```

클라이언트 관점에서 모델링 한 위 예제 코드의 문제
- 클라이언트로 하여금 인증한다는 의미를 이해하도록 요구함.
- 유니쿼터스 언어가 명시적으로 모델링되지 않았음. User 에게 ‘인증 가능 여부’를 물어야 하는데 모델에게 ‘인증하라’고 요청하고 있음.
- 실제로 클라이언트가 수행해야만 하는 비즈니스적 책임은 다른 모든 세부사항을 다룰 단일 도메인 특정 오퍼레이션의 사용을 조정하는 일뿐이어야 함.

```java
// 식별자와 관련된 모든 개념을 identity 모듈 안에 넣음
package com.saasovation.identityaccess.domain.model.identity;

public interface AuthenticationService {
    public UserDescriptor authenticate(TenantId aTenentId,
                                       String aUsername,
                                       String aPassword) {
        // do something
    }
}
```

- 모든 인증 세부 사항을 애플리케이션 서비스 클라이언트에서 `AuthenticationService `라는 무상태 도메인 서비스로 밀어냄.
- `UserDescriptor`라는 User를 참조하기 위해 필수적인 일부 특성만 포함한 값 객체를 반환.
- 따라서 도메인 로직이 애플리케이션 계층으로 유출되지 않음.
