---
layout: post
title:  "yujungSpring1"
author: 이유정
date:   2023-04-13
category: TeamC
icon: spring
keywords: tag1, tag2
preview: 0
---

## 🍀 스프링 핵심 원리 - 기본편

## &nbsp;섹션1. 객체 지향 설계와 스프링

<br/>

## 🍀 스프링이란?
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung1.jpg?raw=true" width="640" height="auto"/>

■ <span style="color:green">스프링 생태계</span>

> ○ 필수
>> 스프링 프레임워크: 스프링 부트를 통해서 스프링 프레임워크의 기술들을 편리하게 사용<br/>
   스프링 부트: 스프링을 편리하게 사용할 수 있도록 지원<br/>

> ○ 선택
>> 스프링 데이터 - CRUD를 편리하게 사용할 수 있도록 도와주는 기술(Spring Data JPA를 가장 많이 사용)<br/>
    스프링 세션 - 세션기능을 편리하게 사용할 수 있도록 도와주는 기술<br/>
    스프링 시큐리티 - 보안과 관련<br/>
    스프링 Rest Docs - API문서화를 편리하게 해주는 기술<br/>
    스프링 배치 - 데이터 배치처리에 특화된 기술<br/>
    스프링 클라우드 - 클라우드 기술에 특화된 기술

<br/>

***
## 🍀 좋은 객체 지향 프로그래밍이란?<br/>

> 객체 지향 특징<br/>
>> 추상화<br/>
>> 캡슐화<br/>
>> 상속<br/>
>> <span style="color:blue"><b>다형성</b></span>

<br/>

### &nbsp;&nbsp;&nbsp;◼ 객체 지향 프로그래밍<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위 <b>객체</b>들의 모임으로 파악하고자 하는 것<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 각각의 <b>객체</b>는 <b>메시지</b>를 주고받고, 데이터를 처리할 수 있다. <b>(협력)</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 객체 지향 프로그래밍은 프로그램을 <b>유연</b>하고 <b>변경</b>이 용이하게 만들기 때문에 대규모 소프트웨어 개발에 많이 사용

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● <b>다형성(Polymorphism)</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 실세계와 객체 지향을 1:1로 매칭X<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 그래도 실세계의 비유로 이해하기에는 좋음<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>역할</b>과 <b>구현</b>으로 세상을 구분<br/>

> [ 장점 ]<br/>
>> <b>클라이언트</b>는 대상의 역할(인터페이스)만 알면 된다.<br/>
>> <b>클라이언트</b>는 구현 대상의 <b>내부 구조를 몰라도</b> 된다.<br/>
>> <b>클라이언트</b>는 구현 대상의 <b>내부 구조가 변경</b>되어도 영향을 받지 않는다.<br/>
>> <b>클라이언트</b>는 구현 <b>대상 자체를 변경</b>해도 영향을 받지 않는다.


<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung2.jpg?raw=true" width="500" height="auto"/>
<br/><br/>

> ○ 다형성의 본질
>> 인터페이스를 구현한 객체 인스턴스를 <b>실행 시점</b>에 <b>유연</b>하게 <b>변경</b>할 수 있다.<br/>
>> 다형성의 본질을 이해하려면 <b>협력</b>이라는 객체사이의 관계에서 시작<br/>
>> <b>클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있다.</b>


<br/><br/>

***

### 🍀 좋은 객체 지향 설계의 5가지 원칙(SOLID)<br/>

### &nbsp;&nbsp;&nbsp;◼ SOLID
&nbsp;&nbsp;&nbsp;&nbsp;: 클린코드로 유명한 로버트 마틴이 좋은 객체 지향 설계의 5가지 원칙을 정리<br/><br/>

```
- SRP: 단일 책임 원칙 (Single Responsibility Principle)
- OCP: 개방-폐쇄 원칙 (Open/Closed Principle)
- LSP: 리스코프 치환 원칙 (Liskov Substitution Principle)
- ISP: 인터페이스 분리 원칙 (Interface segregation principle)
- DIP: 의존관계 역전 원칙 (Dependency Inversion Principle)
```

<br/>
&nbsp;&nbsp;&nbsp;&nbsp;● <b>SRP 단일 책임 원칙 (Single Responsibility Principle)</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 한 클래스는 하나의 책임만 가져야 한다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 하나의 책임이라는 것은 모호하다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 클 수 있고 작을 수 있다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 문맥과 상황에 따라 다르다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>중요한 기준은 변경</b>이다. 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;예) UI변경, 객체의 생성과 사용을 분리<br/>

&nbsp;&nbsp;&nbsp;&nbsp;● <b>OCP 개방-폐쇄 원칙 (Open/Closed Principle) ★</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 소프트웨어 요소는 <b>확장에는 열려</b> 있으나 <b>변경에는 닫혀</b> 있어야 한다..<b>다형성</b> 활용<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ 문제점 ]<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 구현 객체를 변경하려면 클라이언트 코드를 변경해야 한다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 분명 다형성을 사용했지만 OCP원칙을 지킬 수 없다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;→ <b>객체를 생성하고 연관관계를 맺어주는 별도의 조립, 설정자가 필요</b>

&nbsp;&nbsp;&nbsp;&nbsp;● <b>LSP 리스코프 치환 원칙 (Liskov Substitution Principle)</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 다형성에서 하위 클래스는 인터페이스 규약을 다 지켜야 한다는 것<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 다형성을 지원하기 위한 원칙, 인터페이스를 구현한 구현체는 믿고 사용하려면 이 원칙이 필요<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;예) 자동차 인터페이스의 엑셀은 앞으로 가라는 기능.. 뒤로 가게 구현하면 LSP위반<br/>

&nbsp;&nbsp;&nbsp;&nbsp;● <b>ISP 인터페이스 분리 원칙 (Interface segregation principle)</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 자동차 인터페이스 → 운전 인터페이스, 정비 인터페이스로 분리<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 사용자 클라이언트 → 운전자 클라이언트, 정비사 클라이언트로 분리<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 분리하면 정비 인터페이스 자체가 변해도 운전자 클라이언트에 영향을 주지 않는다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 인터페이스가 명확해지고 대체 가능성이 높아진다.<br/>

&nbsp;&nbsp;&nbsp;&nbsp;● <b>DIP 의존관계 역전 원칙 (Dependency Inversion Principle) ★</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 프로그래머는 "추상화에 의존해야지, 구체화에 의존하면 안된다."<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 구현 클래스에 의존하지 말고, 인터페이스에 의존<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 앞에서 이야기한 <b>역할(Role)에 의존하게 해야 한다는 것과 같다.</b> 객체 세상도 클라이언트가 인터페이스에 의존해야 유연하게 구현체를 변경할 수 있다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;구현체에 의존하게 되면 변경이 어려워진다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- OCP에서 설명한 MemberService는 인터페이스에 의존하지만 구현 클래스도 동시에 의존한다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>DIP 위반</b><br/><br/>

```
 ✔ 정리
  - 객체 지향의 핵심은 다형성
  - 다형성 만으로는 쉽게 부품을 갈아 끼우듯이 개발할 수 없다.
  - 다형성 만으로는 구현 객체를 변경할 때 클라이언트 코드도 함께 변경된다.
  - 다형성만으로는 OCP, DIP를 지킬 수 없다..뭔가 더 필요
```

<br/>

### &nbsp;&nbsp;&nbsp;◼ 객체 지향 설계와 스프링

> 스프링-객체 지향<br/>
>> 스프링은 다음 기술로 다형성 + OCP, DIP를 가능하게 지원<br/>
>>> DI(Dependency Injection): 의존관계, 의존성 주입<br/>
>>> DI 컨테이너 제공<br/>
>>> <b>클라이언트 코드의 변경 없이 기능 확장</b><br/>
>>> 쉽게 부품을 교체하듯이 개발

<br/>

```
 ✔ 정리
  - 모든 설계에 역할과 구현을 분리
  - 이상적으로는 모든 설계에 인터페이스를 부여
    인터페이스를 먼저 설계하고 구현을 하면 나중에 바뀌더라도 나머지를 변경할 필요가 없어 변경의 범위가 작고 유연해진다는 장점이 있다.
```

<br/>
