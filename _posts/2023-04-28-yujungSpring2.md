---
layout: post
title:  "yujungSpring2"
author: 이유정
date:   2023-04-28
category: TeamC
icon: spring
keywords: tag1, tag2
preview: 0
---

## 🍀 스프링 핵심 원리 - 기본편

## 섹션2·3. 스프링 핵심 원리 - 객체 지향 원리 적용

<br/>

### ■ AppConfig
  - 애플리케이션의 전체 동작 방식을 구성(config)하기 위해 <b>구현 객체를 생성</b>하고 <b>연결</b>하는 책임을 가진 별도의 설정 클래스

> 애플리케이션의 실제 동작에 필요한 <b>구현 객체를 생성</b>한다.<br/>
> 생성한 객체 인스턴스의 참조(레퍼런스)를 <b>생성자를 통해서 주입(연결)</b>해준다.<br/>
> 관심사의 분리: 객체를 생성하고 연결하는 역할과 실행하는 역할이 명확히 분리되어야 한다.<br/>

<br/>
```
 ✔ 정리
  - AppConfig를 통해 관심사를 확실하게 분리
  - ex) 배역-배우 | 공연기획자:AppConfig
   → AppConfig는 구현 클래스를 선택(배역에 맞는 담당 배우 선택..애플리케이션이 어떻게 동작해야 할지 전체 구성을 책임)
```
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● <b>AppConfig 리펙터링</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 구성 정보에서 역할과 구현을 명확하게 분리<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 역할이 잘 드러남<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 중복 제거<br/><br/>


### ■ 좋은 객체 지향 설계의 5가지 원칙의 적용<br/>

- SRP, DIP, OCP 적용

<br/>
### ● SRP 단일 책임 원칙
&nbsp;&nbsp;<b>: 한 클래스는 하나의 책임만 가져야 한다.</b>
> -&nbsp;클라이언트 객체는 직접 구현 객체를 생성하고 연결, 실행하는 다양한 책임을 가지고 있음<br/>
> -&nbsp;SRP 단일 책임 원칙을 따르면서 관심사를 분리<br/>
> -&nbsp;구현 객체를 생성하고 연결하는 책임은 AppConfig가 담당<br/>
> -&nbsp;클라이언트 객체는 실행하는 책임만 담당

<br/>
### ● DIP 의존관계 역전 원칙
&nbsp;&nbsp;<b>: 프로그래머는 “추상화에 의존해야지, 구체화에 의존하면 안된다.”</b>

<br/>
### ● OCP
&nbsp;&nbsp;<b>: 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.</b>
> -&nbsp;다형성 사용하고 클라이언트가 DIP를 지킴<br/>
> -&nbsp;애플리케이션을 사용 영역과 구성 영역으로 나눔<br/>
> -&nbsp;<b>소프트웨어 요소를 새롭게 확장해도 사용 영역의 변경은 닫혀 있다.</b>

<br/>

### ■ Ioc, DI 컨테이너

<br/>

### ● 제어의 역전 IoC(Inversion of Control)
&nbsp;&nbsp;<b>: 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는 것</b>

&nbsp;&nbsp;&nbsp;○ <b>프레임워크 - 프레임워크가 내가 작성한 코드를 제어하고 대신 실행(JUnit)</b><br/>
&nbsp;&nbsp;&nbsp;○ <b>라이브러리 - 내가 작성한 코드가 직접 제어의 흐름을 담당</b>

<br/>

### ● 의존관계 주입 DI(Dependency Injection)
&nbsp;&nbsp;- 의존관계는 <b>정적인 클래스 의존 관계와, 실행 시점에 결정되는 동적인 객체(인스턴스) 의존 관계</b> 둘을 분리해서 생각해야 한다.

<br/>

### ● IoC 컨테이너, DI 컨테이너
> AppConfig 처럼 객체를 생성하고 관리하면서 의존관계를 연결해 주는 것<br/>
> 의존관계 주입에 초점을 맞추어 최근에는 주로 DI 컨테이너<br/>
> 또는 어샘블러, 오브젝트 팩토리 등으로 불리기도 한다.

<br/>

### ■ 스프링 기반 AppConfig<br/>

```
@Configuration
public class AppConfig {
 @Bean
 public MemberService memberService() {
 	return new MemberServiceImpl(memberRepository());
 }
 
 @Bean
 public OrderService orderService() {
 	return new OrderServiceImpl(
 	memberRepository(),
 	discountPolicy());
 }
 
 @Bean
 public MemberRepository memberRepository() {
 	return new MemoryMemberRepository();
 }
 
 @Bean
 public DiscountPolicy discountPolicy() {
 	return new RateDiscountPolicy();
 }
 
}
```
> -&nbsp;AppConfig에 설정을 구성한다는 뜻의 `@Configuration`을 붙여준다.<br/>
> -&nbsp;각 메서드에 `@Bean`을 붙여준다.. 스프링 컨테이너에 스프링 빈으로 등록<br/>

<br/>

### ■ 스프링 컨테이너<br/>

> -`@Bean`이라 적힌 메서드를 모두 호출해서 반한된 객체를 스프링 컨테이너에 등록(등록된 객체: 스프링 빈)<br/>
> -스프링 빈은 `@Bean`이 붙은 메서드의 명을 스프링 빈의 이름으로 사용<br/>
> -스프링 빈은 `applicationContext.getBean()` 메서드를 사용해서 찾을 수 있다.

<br/>

***

## 섹션4. 스프링 컨테이너와 스프링 빈

<br/>

### ■ 스프링 컨테이너 생성과정

```
//스프링 컨테이너 생성
ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class)
```
- `ApplicationContext`: 스프링 컨테이너 / 인터페이스
- 스프링 컨테이너는 XML을 기반으로 만들 수 있고, 애노테이션 기반의 자바 설정 클래스로 만들 수 있다.



1. 스프링 컨테이너 생성
2. 스프링 빈 등록<br/>
  ● 빈 이름<br/>
  &nbsp;&nbsp;&nbsp;- 빈 이름은 메서드 이름을 사용<br/>
  &nbsp;&nbsp;&nbsp;- 빈 이름을 직접 부여할 수도 있다.. `@Bean(name="memberService2")`<br/>
  ** <b>빈 이름은 항상 다른 이름을 부여해야 한다</b> **

3. 스프링 빈 의존관계 설정 - 준비
4. 스프링 빈 의존관계 설정 - 완료<br/>
&nbsp;- 스프링 컨테이너는 설정 정보를 참고해서 의존관계를 주입(DI)<br/>

<br/>
### ■ 스프링 빈 조회 - 기본
- `ac.getBean(빈이름, 타입)`
- `ac.getBean(타입)`
- 조회 대상 스프링 빈이 없으면 예외 발생<br/>
 `NoSuchBeanDefinitionException: No bean named 'xxxxx' available`
 

```
class ApplicationContextBasicFindTest {
 AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);
 
 @Test
 @DisplayName("빈 이름으로 조회")
 void findBeanByName() {
 	MemberService memberService = ac.getBean("memberService",MemberService.class);
 	assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
 }
 
 @Test
 @DisplayName("이름 없이 타입만으로 조회")
 void findBeanByType() {
 	MemberService memberService = ac.getBean(MemberService.class);
 	assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
 }
 
 @Test
 @DisplayName("구체 타입으로 조회")
 void findBeanByName2() {
 	MemberServiceImpl memberService = ac.getBean("memberService",MemberServiceImpl.class);
 	assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
 }
 
 @Test
 @DisplayName("빈 이름으로 조회X")
 void findBeanByNameX() {
 	//ac.getBean("xxxxx", MemberService.class);
 	Assertions.assertThrows(NoSuchBeanDefinitionException.class, () ->
	ac.getBean("xxxxx", MemberService.class));
 }
 
}
```

<br/>
### ■ 스프링 빈 조회 - 동일한 타입이 둘 이상
- 타입으로 조회시 같은 타입의 스프링 빈이 둘 이상이면 오류가 발생
- `ac.getBeansOfType()`을 사용하면 해당 타입의 모든 빈을 조회가능


<br/>
### ■ 스프링 빈 조회 - 상속 관계
- 부모 타입으로 조회하면 자식 타입도 함께 조회


<br/>
### ■ BeanFactory와 ApplicationContext

#### ● BeanFactory
&nbsp;&nbsp;- 스프링 컨테이너의 최상위 인터페이스<br/>
&nbsp;&nbsp;- 스프링 빈을 관리하고 조회하는 역할을 담당<br/>
&nbsp;&nbsp;- `getBean()`을 제공

<br/>

#### ● ApplicationContext
&nbsp;&nbsp;- BeanFactory 기능을 모두 상속받아서 제공

&nbsp;&nbsp;&nbsp;○ <b>ApplicatonContext가 제공하는 부가기능</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>메시지소스를 활용한 국제화 기능</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(한국-한국어, 영어권-영어)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>환경변수</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(로컬, 개발, 운영등을 구분해서 처리)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>애플리케이션 이벤트</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(이벤트를 발행하고 구독하는 모델을 편리하게 지원)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>편리한 리소스 조회</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(파일, 클래스패스, 외부 등에서 리소스를 편리하게 조회)<br/><br/>


```
 ✔ 정리
  - ApplicationContext는 BeanFactory의 기능을 상속받는다.
  - ApplicationContext는 빈 관리기능 + 편리한 부가 기능을 제공
  - BeanFactory보다 부가기능이 포함된 ApplicationContext를 사용
  - BeanFactory나 ApplicationContext를 스프링 컨테이너라고 한다.
```

<br/>
### ■ 스프링 빈 설정 메타 정보 - BeanDefinition
&nbsp;: 역할과 구현을 개념적으로 나눈 것
<br/><br/>

#### &nbsp;● <b>BeanDefinition 정보</b>

> -&nbsp;BeanClassName: 생성할 빈의 클래스 명(자바 설정 처럼 팩토리 역할의 빈을 사용하면 없음)<br/>
> -&nbsp;factoryBeanName: 팩토리 역할의 빈을 사용할 경우 이름. 예) appConfig<br/>
> -&nbsp;factoryMethodName: 빈을 생성할 팩토리 메서드 지정. 예) memberService<br/>
> -&nbsp;Scope: 싱글톤(기본값)<br/>
> -&nbsp;lazyInit: 스프링 컨테이너를 생성할 때 빈을 생성하는 것이 아니라, 실제 빈을 사용할 때까지 최대한
 생성을 지연처리 하는지 여부<br/>
> -&nbsp;InitMethodName: 빈을 생성하고, 의존관계를 적용한 뒤에 호출되는 초기화 메서드 명<br/>
> -&nbsp;DestroyMethodName: 빈의 생명주기가 끝나서 제거하기 직전에 호출되는 메서드 명<br/>
> -&nbsp;Constructor arguments, Properties: 의존관계 주입에서 사용(자바 설정처럼 팩토리 역할의 빈을 사용하면 없음)

<br/>

***

## 섹션5. 싱글톤 컨테이너

<br/>

### ■ 싱글톤 패턴
- 클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴
- 객체 인스턴스를 2개 이상 생성하지 못하도록 막아야 한다.<br/>
 -&nbsp;private 생성자를 사용(외부에서 임의로 new 키워드를 사용하지 못하도록)<br/>
  &nbsp;&nbsp;호출할 때 마다 같은 객체 인스턴스를 반환하는 것을 확인할 수 있다.

&nbsp;&nbsp;[ 문제점 ]<br/>
> ① 싱글톤 패턴을 구현하는 코드 자체가 많이 들어간다.<br/>
> ② 의존관계상 클라이언트가 구체 클래스에 의존 → DIP 위반<br/>
> ③ 클라이언트가 구체 클래스에 의존해서 OCP 원칙을 위반할 가능성이 높다.<br/>
> ④ 테스트·내부 속성을 변경하거나 초기화 하기 어렵다.<br/>
> ⑤ private 생성자로 자식 클래스를 만들기 어렵다.<br/>
> ⑥ 결론적으로 유연성이 떨어진다.<br/>
> ⑦ 안티패턴으로 불리기도 한다.

<br/>
### ■ 싱글톤 컨테이너
&nbsp;&nbsp;&nbsp;- 스프링 컨테이너는 싱글턴 패턴을 적용하지 않아도 객체 인스턴스를 싱글톤으로 관리<br/>
&nbsp;&nbsp;&nbsp;- 스프링 컨테이너는 싱글톤 컨테이너 역할..싱글톤 객체를 생성하고 관리하는 기능을 싱글톤레지스트리라 한다.<br/>
&nbsp;&nbsp;&nbsp;- 싱글톤 패턴의 모든 단점을 해결하면서 객체를 싱글톤으로 유지할 수 있다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;→ 싱글톤 패턴을 위한 지저분한 코드가 들어가지 않아도 된다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;→ DIP, OCP, 테스트, private 생성자로 부터 자유롭게 싱글톤을 사용할 수 있다.<br/><br/>

### &nbsp;● 싱글톤 방식의 주의점

> -&nbsp;싱글톤 패턴이든 스프링 같은 싱글톤 컨테이너를 사용하든 객체 인스턴스를 하나만 생성해서 공유하는 싱글톤 방식은 여러 클라이언트가<br/>
&nbsp;하나의 같은 객체 인스턴스를 공유하기 때문에 싱글톤 객체는 상태를 유지(stateful)하게 설계하면 안된다.<br/>
> -&nbsp;스프링 빈의 필드에 공유 값을 설정하면 큰 장애가 발생할 수 있다.<br/><br/>
> -&nbsp;무상태(stateless)로 설계<br/>
>> -&nbsp;특정 클라이언트에 의존적인 필드가 있으면 안된다.<br/>
>> -&nbsp;특정 클라이언트가 값을 변경할 수 있는 필드가 있으면 안된다.<br/>
>> -&nbsp;가급적 읽기만 가능해야 한다.<br/>
>> -&nbsp;필드 대신에 자바에서 공유되지 않는 지역변수, 파라미터, ThreadLocal 등을 사용해야 한다.

<br/>
### ■ @Configuration과 싱글톤
<br/>
```
 ✔ 정리
  - @Bean만 사용해도 스프링 빈으로 등록되지만, 싱글톤을 보장하지 않는다.
  - 스프링 설정 정보는 @Configuration 을 사용
```

<br/>

***

## 섹션6. 컴포넌트 스캔

<br/>

### ■ 컴포넌트 스캔과 의존관계 자동 주입
&nbsp;&nbsp;&nbsp;- 스프링은 설정 정보가 없어도 자동으로 스프링 빈을 등록하는 컴포넌트 스캔이라는 기능
제공<br/>
&nbsp;&nbsp;&nbsp;- 의존관계를 자동으로 주입하는 `@Autowired` 라는 기능 제공<br/>

#### &nbsp;● OrderServiceImpl @Component, @Autowired 추가

```
@Component
public class OrderServiceImpl implements OrderService {
 private final MemberRepository memberRepository;
 private final DiscountPolicy discountPolicy;
 
 @Autowired
 public OrderServiceImpl(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
 	this.memberRepository = memberRepository;
 	this.discountPolicy = discountPolicy;
 }
}
```
&nbsp;* @Autowired 를 사용하면 생성자에서 여러 의존관계도 한번에 주입받을 수 있다.<br/>

1. @ComponentScan<br/>

> -`@ComponentScan`은 `@Component`가 붙은 모든 클래스를 스프링 빈으로 등록<br/>
> -스프링 빈의 기본 이름은 클래스명을 사용하되 맨 앞글자만 소문자를 사용
>> <b>빈 이름 기본 전략:</b> MemberServiceImpl 클래스 → memberServiceImpl<br/>
>> <b>빈 이름 직접 지정:</b> 스프링 빈의 이름을 직접 지정하고 싶으면 ex)&nbsp;`@Component("memberService2")`로 이름부여


<br/>
2. @Autowired 의존관계 자동 주입<br/>

> -생성자에 `@Autowired`를 지정하면 스프링 컨테이너가 자동으로 해당 스프링 빈을 찾아서 주입<br/>
> -이때 기본 조회 전략은 타입이 같은 빈을 찾아서 주입
>> -`getBean(MemberRepository.class)`와 동일하다고 이해하면 된다.<br/>
>> -생성자에 파라미터가 많아도 다 찾아서 자동으로 주입한다.

<br/>
### ■ 탐색 위치와 기본 스캔 대상
#### &nbsp;● 탐색할 패키지의 시작 위치 지정
```
@ComponentScan(
 	basePackages = "hello.core",
}
```

&nbsp;&nbsp;&nbsp;- `basePackages`: 탐색할 패키지의 시작 위치를 지정.. 이 패키지를 포함해서 하위 패키지를 모두 탐색한다.<br/>
&nbsp;&nbsp;&nbsp;- `basePackages = {"hello.core", "hello.service"}`: 여러 시작 위치를 지정할 수도
있다.<br/>
&nbsp;&nbsp;&nbsp;- `basePackageClasses`: 지정한 클래스의 패키지를 탐색 시작 위치로 지정<br/>
&nbsp;&nbsp;&nbsp;- 만약 지정하지 않으면 `@ComponentScan`이 붙은 설정 정보 클래스의 패키지가 시작 위치가 된다.

<br/>
&nbsp;* 권장하는 방법<br/>
&nbsp;&nbsp;&nbsp;- 설정 정보 클래스의 위치를 프로젝트 최상단에 두는 것 (스프링 부트가 기본으로 제공하는 방법)<br/>

ex) `com.hello`→ 프로젝트 시작 루트. 여기에 AppConfig 같은 메인 설정 정보를 두고 @ComponentScan 애노테이션을 붙이고, `basePackages` 지정은 생략

<br/>
### &nbsp;● 컴포넌트 스캔 기본 대상
&nbsp;&nbsp;&nbsp;- `@Component`: 컴포넌트 스캔에서 사용<br/>
&nbsp;&nbsp;&nbsp;- `@Controlller`: 스프링 MVC 컨트롤러에서 사용<br/>
&nbsp;&nbsp;&nbsp;- `@Service`: 스프링 비즈니스 로직에서 사용<br/>
&nbsp;&nbsp;&nbsp;- `@Repository`: 스프링 데이터 접근 계층에서 사용<br/>
&nbsp;&nbsp;&nbsp;- `@Configuration`: 스프링 설정 정보에서 사용<br/>

&nbsp;* 컴포넌트 스캔의 용도 뿐만 아니라 애노테이션이 있으면 스프링은 부가 기능을 수행 *<br/>
&nbsp;&nbsp;&nbsp;- `@Controlller`: 스프링 MVC 컨트롤러로 인식<br/>
&nbsp;&nbsp;&nbsp;- `@Service`: 특별한 처리를 하지 않는다.. 대신 개발자들이 핵심 비즈니스 계층을 인식하는데 도움이 된다<br/>
&nbsp;&nbsp;&nbsp;- `@Repository`: 스프링 데이터 접근 계층으로 인식하고, 데이터 계층의 예외를 스프링 예외로 변환<br/>
&nbsp;&nbsp;&nbsp;- `@Configuration`: 스프링 설정 정보로 인식하고, 스프링 빈이 싱글톤을 유지하도록 추가
처리<br/>

> `useDefaultFilters`옵션은 기본으로 켜져있는데 이 옵션을 끄면 기본 스캔 대상들이 제외된다.

<br/>
### ■ 필터
&nbsp;&nbsp;&nbsp;- `includeFilters`: 컴포넌트 스캔 대상을 추가로 지정<br/>
&nbsp;&nbsp;&nbsp;- `excludeFilters`: 컴포넌트 스캔에서 제외할 대상을 지정<br/>

<br/>
### &nbsp;● FilterType 옵션
&nbsp;&nbsp;&nbsp;- ANNOTATION: 기본값, 애노테이션을 인식해서 동작<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) `org.example.SameAnnotation`<br/>
&nbsp;&nbsp;&nbsp;- ASSIGNABLE_TYPE: 지정한 타입과 자식 타입을 인식해서 동작<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) `org.example.SomeClass`<br/>
&nbsp;&nbsp;&nbsp;- ASPECTJ: AspectJ 패턴 사용<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) `org.example..*Service+`<br/>
&nbsp;&nbsp;&nbsp;- REGEX: 정규 표현식<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) `org\.example\.Default.*`<br/>
&nbsp;&nbsp;&nbsp;- CUSTOM: TypeFilter 이라는 인터페이스를 구현해서 처리<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) `org.example.MyTypeFilter`<br/>

<br/>
### ■ 중복 등록과 충돌
1. 자동 빈 등록 vs 자동 빈 등록<br/>
컴포넌트 스캔에 의해 자동으로 스프링 빈이 등록되는데, 그 이름이 같은 경우 스프링 오류발생<br/>
&nbsp;-`ConflictingBeanDefinitionException` 예외 발생

2. 수동 빈 등록 vs 자동 빈 등록<br/>


&nbsp;&nbsp;&nbsp;* 수동 빈 등록시 남는 로그 *
> Overriding bean definition for bean 'memoryMemberRepository' with a different definition: replacing


&nbsp;&nbsp;&nbsp;* 수동 빈 등록, 자동 빈 등록 오류시 스프링 부트 에러 *
> Consider renaming one of the beans or enabling overriding by setting spring.main.allow-bean-definition-overriding=true

<br/>

***

## 섹션7. 의존관계 자동 주입

<br/>

### ■ 다양한 의존관계 주입 방법
<br/>
### &nbsp;● 생성자 주입
&nbsp;&nbsp;: 생성자를 통해서 의존 관계를 주입 받는 방법
> [ 특징 ]<br/>
>> 생성자 호출시점에 딱 1번만 호출되는 것이 보장된다.<br/>
>> <b>불변, 필수</b> 의존관계에 사용<br/>
>> <b>★ 생성자가 딱 1개만 있으면 @Autowired를 생략해도 자동 주입 된다.</b> (스프링 빈에만 해당)<br/>

<br/>
### &nbsp;● 수정자 주입(setter 주입)
&nbsp;&nbsp;: setter라 불리는 필드의 값을 변경하는 수정자 메서드를 통해서 의존관계를 주입하는 방법
> [ 특징 ]<br/>
>> <b>선택, 변경</b> 가능성이 있는 의존관계에 사용<br/>
>> 자바빈 프로퍼티 규약의 수정자 메서드 방식을 사용하는 방법<br/>

```
❗ @Autowired의 기본동작은 주입할 대상이 없으면 오류가 발생
  주입할 대상이 없어도 동작하게 하려면 @Autowired(required = false)로 지정하면 된다.
```

<br/>
### &nbsp;● 필드 주입
&nbsp;&nbsp;: 필드에 바로 주입하는 방법
> [ 특징 ]<br/>
>> 외부에서 변경이 불가능해서 테스트 하기 힘들다는 단점이 있다.<br/>
>> DI 프레임워크가 없으면 아무것도 할 수 없다.<br/>
>> 스프링 설정을 목적으로 하는 `@Configuration` 같은 곳에서만 특별한 용도로 사용<br/>

<br/>
### &nbsp;● 일반 메서드 주입
&nbsp;&nbsp;: 일반 메서드를 통해서 주입 받을 수 있다.
> [ 특징 ]<br/>
>> 한번에 여러 필드를 주입 받을 수 있다.<br/>
>> 일반적으로 잘 사용하지 않는다.<br/>

<br/>

### ■ 옵션 처리
> 자동 주입 대상을 옵션으로 처리하는 방법
>> `@Autowired(required=false)`: 자동 주입할 대상이 없으면 수정자 메서드 자체가 호출 안됨<br/>
>> `org.springframework.lang.@Nullable`: 자동 주입할 대상이 없으면 null이 입력된다.<br/>
>> `Optional<>`: 자동 주입할 대상이 없으면 `Optional.empty`가 입력된다.

<br/>
### &nbsp;● 불변

- 대부분의 의존관계 주입은 한번 일어나면 애플리케이션 종료시점까지 의존관계를 변경할 일이 없다. 
- 오히려 대부분의 의존관계는 애플리케이션 종료 전까지 변하면 안된다.(불변)
- 수정자 주입을 사용하면, setXxx 메서드를 public으로 열어두어야 한다.
- 누군가 실수로 변경할 수도 있고, 변경하면 안되는 메서드를 열어두는 것은 좋은 설계 방법이 아니다.
- 생성자 주입은 객체를 생성할 때 딱 1번만 호출되므로 이후에 호출되는 일이 없다. 따라서 불변하게 설계할 수 있다.


<br/>
### &nbsp;● final 키워드
&nbsp;&nbsp;: 생성자 주입을 사용하면 필드에 `final` 키워드를 사용할 수 있다.

<br/>

```
 ✔ 정리
  - 기본으로 생성자 주입을 사용하고, 필수 값이 아닌 경우에는 수정자 주입 방식을 옵션으로 부여하면 된다. 
  - 생성자 주입과 수정자 주입을 동시에 사용할 수 있다.
  - 항상 생성자 주입을 선택.. 가끔 옵션이 필요하면 수정자 주입 선택
```

<br/>

### ■ 롬복
> 롬복 라이브러리가 제공하는 `@RequiredArgsConstructor` 기능을 사용하면 final이 붙은 필드를 모아서
생성자를 자동으로 만들어준다.


<br/>

### ■ @Autowired 필드 명, @Qualifier, @Primary

#### &nbsp;● 조회 대상 빈이 2개 이상일 때 해결 방법
&nbsp;&nbsp;&nbsp;① @Autowired 필드 명 매칭<br/>
&nbsp;&nbsp;&nbsp;② @Qualifier → @Qualifier끼리 매칭 → 빈 이름 매칭<br/>
&nbsp;&nbsp;&nbsp;③ @Primary 사용<br/>

<br/>

&nbsp;&nbsp;&nbsp;<b>1. @Autowired 필드 명 매칭</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: 타입 매칭을 시도하고, 이때 여러 빈이 있으면 필드 이름, 파라미터 이름으로 빈 이름을 추가 매칭<br/>

```
- 기존 코드
@Autowired
private DiscountPolicy discountPolicy

***

- 필드 명을 빈 이름으로 변경
@Autowired
private DiscountPolicy rateDiscountPolicy
```

<br/>
&nbsp;&nbsp;&nbsp;<b>2. @Qualifier 사용</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: 추가 구분자를 붙여주는 방법.. 주입 시 추가적인 방법을 제공하는 것이지 빈 이름을 변경하는 것은 X
<br/>

```
- 빈 등록시 @Qualifier를 붙여 준다.
@Component
@Qualifier("mainDiscountPolicy")
public class RateDiscountPolicy implements DiscountPolicy {}

***

① @Qualifier끼리 매칭
② 빈 이름 매칭
③ NoSuchBeanDefinitionException 예외발생
④ 모든 코드에 @Qualifier를 붙여주어야 한다는 단점
```

<br/>
&nbsp;&nbsp;&nbsp;<b>3. @Primary 사용</b><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: 우선순위를 정하는 방법.. @Autowired 시에 여러 빈이 매칭되면 @Primary 가 우선권을 가진다.
<br/>

```
- 사용 코드

//생성자
@Autowired
public OrderServiceImpl(MemberRepository memberRepository,
 DiscountPolicy discountPolicy) {
 this.memberRepository = memberRepository;
 this.discountPolicy = discountPolicy;
}

//수정자
@Autowired
public DiscountPolicy setDiscountPolicy(DiscountPolicy discountPolicy) {
 this.discountPolicy = discountPolicy;
}
```

<br/>

### ■ 조회한 빈이 모두 필요할 때 - List, Map
&nbsp;&nbsp;: `@Qualifier("mainDiscountPolicy")`- 문자를 적으면 컴파일시 타입 체크가 안된다. 

```
ex)

public class AllBeanTest {

 @Test
 void findAllBean() {
 	ApplicationContext ac = new AnnotationConfigApplicationContext(AutoAppConfig.class,DiscountService.class);
 	DiscountService discountService = ac.getBean(DiscountService.class);
 	Member member = new Member(1L, "userA", Grade.VIP);
 	int discountPrice = discountService.discount(member, 10000,"fixDiscountPolicy");
 	assertThat(discountService).isInstanceOf(DiscountService.class);
 	assertThat(discountPrice).isEqualTo(1000);
 }
 
 static class DiscountService {
 	private final Map<String, DiscountPolicy> policyMap;
 	private final List<DiscountPolicy> policies;
 	public DiscountService(Map<String, DiscountPolicy> policyMap, List<DiscountPolicy> policies) {
 		this.policyMap = policyMap;
 		this.policies = policies;
 		System.out.println("policyMap = " + policyMap);
 		System.out.println("policies = " + policies);
 	}
    
   public int discount(Member member, int price, String discountCode) {
      DiscountPolicy discountPolicy = policyMap.get(discountCode);
      System.out.println("discountCode = " + discountCode);
      System.out.println("discountPolicy = " + discountPolicy);
      return discountPolicy.discount(member, price);
   }
 }
}
```

<br/>

### &nbsp;● 로직 분석
> -&nbsp;DiscountService는 Map으로 모든 DiscountPolicy를 주입받는데 이때 `fixDiscountPolicy`,`rateDiscountPolicy` 가 주입된다.<br/>
> -&nbsp;`discount()` 메서드는 discountCode로 fixDiscountPolicy"가 넘어오면 map에서 `fixDiscountPolicy`스프링 빈을 찾아서 실행.. <br/>&nbsp;&nbsp;"rateDiscountPolicy"가 넘어오면 `rateDiscountPolicy`스프링 빈을 찾아서 실행

<br/>

### &nbsp;● 주입 분석
> -&nbsp;`Map<String, DiscountPolicy>`: map의 키에 스프링 빈의 이름을 넣어주고 그 값으로 `DiscountPolicy`타입으로 조회한 모든 스프링 빈을 담아준다.<br/>
> -&nbsp;`List<DiscountPolicy>`: `DiscountPolicy` 타입으로 조회한 모든 스프링 빈을 담아준다.<br/>
> -&nbsp;해당하는 타입의 스프링 빈이 없으면 빈 컬렉션이나 Map을 주입

<br/>
*<b> 스프링 컨테이너를 생성하면서 스프링 빈 등록하기</b>
- 생성자에 클래스 정보를 넘기면 해당 클래스가 스프링 빈으로 자동 등록<br/>
  `new AnnotationConfigApplicationContext(AutoAppConfig.class,DiscountService.class);`<br/>
  ① `new AnnotationConfigApplicationContext()` 를 통해 스프링 컨테이너를 생성<br/>
  ② `AutoAppConfig.class`, `DiscountService.class`를 파라미터로 넘기면서 해당 클래스를 자동으로 스프링 빈으로 등록

<br/>

***

## 섹션8. 빈 생명주기 콜백

<br/>

### &nbsp;● 스프링 빈의 라이프사이클
> 객체 생성 → 의존관계 주입

<br/>

### &nbsp;● 스프링 빈의 이벤트 라이프사이클
> 스프링 컨테이너 생성 → 스프링 빈 생성 → 의존관계 주입 → 초기화 콜백 → 사용 → 소멸전 콜백 → 스프링
종료

* 초기화 콜백: 빈이 생성되고 빈의 의존관계 주입이 완료된 후 호출
* 소멸전 콜백: 빈이 소멸되기 직전에 호출


<br/>

```
- 스프링이 지원하는 빈 생명주기 콜백
  ① 인터페이스(InitializingBean, DisposableBean)
  ② 설정 정보에 초기화 메서드, 종료 메서드 지정
  ③ @PostConstruct, @PreDestroy 애노테이션 지원
```

<br/>

### ■ 인터페이스 InitializingBean, DisposableBean

```
public class NetworkClient implements InitializingBean, DisposableBean {
 private String url;
 
 public NetworkClient() {
 	System.out.println("생성자 호출, url = " + url);
 }
 
 public void setUrl(String url) {
 	this.url = url;
 }
 
 //서비스 시작시 호출
 public void connect() {
 	System.out.println("connect: " + url);
 }
 
 public void call(String message) {
 	System.out.println("call: " + url + " message = " + message);
 }
 
 //서비스 종료시 호출
 public void disConnect() {
 	System.out.println("close + " + url);
 }
 
 @Override
 public void afterPropertiesSet() throws Exception {
 	connect();
 	call("초기화 연결 메시지");
 }
 
 @Override
 public void destroy() throws Exception {
 	disConnect();
 }
}
```

- `InitializingBean`은 `afterPropertiesSet()` 메서드로 초기화를 지원<br/>
- `DisposableBean`은 `destory()`메서드로 소멸을 지원<br/><br/>
- <b>초기화, 소멸 인터페이스 단점</b><br/>
   -&nbsp;스프링 전용 인터페이스로 해당 코드가 스프링 전용 인터페이스에 의존<br/>
   -&nbsp;초기화, 소멸 메서드의 이름을 변경할 수 없다.<br/>
   -&nbsp;직접 코드를 고칠 수 없는 외부 라이브러리에 적용할 수 없다.
   
<br/>

### ■ 빈 등록 초기화, 소멸 메서드 지정
&nbsp;&nbsp;: `@Bean(initMethod = "init", destroyMethod = "close")`처럼 초기화, 소멸 메서드 지정 가능

<br/>

### &nbsp;● 설정 정보 사용 특징
> -&nbsp;메서드 이름을 자유롭게 줄 수 있다.<br/>
> -&nbsp;스프링 빈이 스프링 코드에 의존하지 않는다.<br/>
> -&nbsp;코드가 아니라 설정 정보를 사용하기 때문에 코드를 고칠 수 없는 외부 라이브러리에도 초기화, 종료
메서드를 적용 가능

<br/>

### &nbsp;● 종료 메서드 추론
> -&nbsp;`@Bean의 destroyMethod` 속성<br/>
> -&nbsp;라이브러리는 대부분 `close`, `shutdown`이라는 이름의 종료 메서드를 사용<br/>
> -&nbsp;@Bean의 `destroyMethod`는 기본값이 `(inferred)`(추론)으로 등록되어 있다.<br/>
> -&nbsp;`close`, `shutdown`이라는 이름의 메서드를 자동으로 호출.. 종료 메서드를 추론해서 호출<br/>
> -&nbsp;직접 스프링 빈으로 등록하면 종료 메서드는 따로 적어주지 않아도 잘 동작한다.<br/>
> -&nbsp;추론 기능을 사용하지 않으려면 `destoryMethod=""`처럼 빈 공백 지정

<br/>

### ■ 애노테이션 @PostConstruct, @PreDestroy
&nbsp;&nbsp;: `@PostConstruct`, `@PreDesstroy` 두 애노테이션을 사용하면 편리하게 초기화와 종료 실행가능

<br/>

#### &nbsp;● @PostConstruct, @PreDestroy 애노테이션 특징
> -&nbsp;최신 스프링에서 가장 권장하는 방법<br/>
> -&nbsp;애노테이션 하나만 붙이면 되므로 매우 편리<br/>
> -&nbsp;`javax.annotation.PostConstruct`스프링에 종속적인 기술이 아니라 JSR-250이라는 자바 표준이기 때문에 스프링이 아닌 다른 컨테이너에서도 동작한다.<br/>
> -&nbsp;컴포넌트 스캔과 잘 어울린다.<br/>
> -&nbsp;직접 스프링 빈으로 등록하면 종료 메서드는 따로 적어주지 않아도 잘 동작한다.<br/>
> -&nbsp;유일한 단점은 외부 라이브러리에는 적용하지 못한다는 것

<br/>

```
 ✔ 정리
  - @PostConstruct, @PreDestroy 애노테이션을 사용
  - 코드를 고칠 수 없는 외부 라이브러리를 초기화, 종료해야 하면 @Bean 의 initMethod, destroyMethod 를 사용
```
   
<br/>

***

## 섹션9. 빈 스코프
&nbsp;&nbsp;* 스코프: 빈이 존재할 수 있는 범위

<br/>

### &nbsp;● 스프링이 지원하는 다양한 스코프
> -&nbsp;<b>싱글톤</b>: 기본 스코프, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프<br/>
> -&nbsp;<b>프로토타입</b>: 스프링 컨테이너는 프로토타입 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 짧은 범위의 스코프<br/><br/>
> -&nbsp;<b>웹 관련 스코프</b>
>> -<b>request</b>: 웹 요청이 들어오고 나갈 때까지 유지되는 스코프<br/>
>> -<b>session</b>: 웹 세션이 생성되고 종료될 때까지 유지되는 스코프<br/>
>> -<b>application</b>: 웹의 서블릿 컨텍스트와 같은 범위로 유지되는 스코프

<br/>

### ■ 프로토타입 스코프

<br/>

### &nbsp;● 싱글톤 빈 요청
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung3.jpg?raw=true" width="640" height="auto"/>

> ① 싱글톤 스코프의 빈을 스프링 컨테이너에 요청<br/>
> ② 스프링 컨테이너는 본인이 관리하는 스프링 빈을 반환<br/>
> ③ 이후에 스프링 컨테이너에 같은 요청이 와도 같은 객체 인스턴스의 스프링 빈을 반환

<br/>

### &nbsp;● 프로토타입 빈 요청
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung4.jpg?raw=true" width="640" height="auto"/>&nbsp;&nbsp;
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung5.jpg?raw=true" width="640" height="auto"/>

> ① 프로토타입 스코프의 빈을 스프링 컨테이너에 요청<br/>
> ② 스프링 컨테이너는 이 시점에 프로토타입 빈을 생성하고 필요한 의존관계를 주입<br/>
> ③ 스프링 컨테이너는 생성한 프로토타입 빈을 클라이언트에 반환<br/>
> ④ 이후에 스프링 컨테이너에 같은 요청이 오면 항상 새로운 프로토타입 빈을 생성해서 반환

<br/>

```
 ✔ 정리
  - 스프링 컨테이너는 프로토타입 빈을 생성하고 의존관계 주입, 초기화까지만 처리
  - 클라이언트에 빈을 반환하고, 이후 스프링 컨테이너는 생성된 프로토타입 빈을 관리하지 않는다.
  - 그래서 @PreDestroy 같은 종료 메서드가 호출되지 않는다.
```
   
<br/>

### &nbsp;● 프로토타입 빈의 특징 정리
> -&nbsp;스프링 컨테이너에 요청할 때 마다 새로 생성<br/>
> -&nbsp;스프링 컨테이너는 프로토타입 빈의 생성과 의존관계 주입 그리고 초기화까지만 관여<br/>
> -&nbsp;종료 메서드가 호출되지 않는다.<br/>
>  -&nbsp;프로토타입 빈은 프로토타입 빈을 조회한 클라이언트가 관리해야 한다. 종료 메서드에 대한 호출도
클라이언트가 직접 해야한다.

<br/>

### ■ 프로토타입 스코프 - 싱글톤 빈과 함께 사용시 문제점

<br/>

### &nbsp;● 스프링 컨테이너에 프로토타입 빈 직접 요청1
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung6.jpg?raw=true" width="640" height="auto"/>

> ① 클라이언트A는 스프링 컨테이너에 프로토타입 빈을 요청<br/>
> ② 스프링 컨테이너는 프로토타입 빈을 새로 생성해서 반환(x01).. 해당 빈의 count 필드 값은 0<br/>
> ③ 클라이언트는 조회한 프로토타입 빈에 addCount() 를 호출하면서 count 필드를 +1<br/>
> -&nbsp;결과적으로 프로토타입 빈(x01)의 count는 1

<br/>

### &nbsp;● 스프링 컨테이너에 프로토타입 빈 직접 요청2
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung7.jpg?raw=true" width="640" height="auto"/>

> ① 클라이언트B는 스프링 컨테이너에 프로토타입 빈을 요청<br/>
> ② 스프링 컨테이너는 프로토타입 빈을 새로 생성해서 반환(x02).. 해당 빈의 count 필드 값은 0<br/>
> ③ 클라이언트는 조회한 프로토타입 빈에 addCount() 를 호출하면서 count 필드를 +1<br/>
> -&nbsp;결과적으로 프로토타입 빈(x02)의 count는 1

<br/>

### &nbsp;● 싱글톤에서 프로토타입 빈 사용
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung8.jpg?raw=true" width="640" height="auto"/>&nbsp;&nbsp;
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung9.jpg?raw=true" width="640" height="auto"/>&nbsp;&nbsp;
<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/springYujung10.jpg?raw=true" width="640" height="auto"/>

> -&nbsp;`clientBean`은 싱글톤이므로 보통 스프링 컨테이너 생성 시점에 함께 생성.. 의존관계 주입도 발생<br/>
> ① `clientBean`은 의존관계 자동 주입을 사용.. 주입 시점에 스프링 컨테이너에 프로토타입 빈을
요청<br/>
> ② 스프링 컨테이너는 프로토타입 빈을 생성해서 clientBean 에 반환.. 프로토타입 빈의 count 필드
값은 0<br/>
> -&nbsp;`clientBean` 은 프로토타입 빈을 내부 필드에 보관(참조값을 보관)<br/>
> -&nbsp;클라이언트 A는 `clientBean`을 스프링 컨테이너에 요청해서 받는다.싱글톤이므로 항상 같은
`clientBean`이 반환된다.<br/>
> ③ 클라이언트 A는 `clientBean.logic()`을 호출<br/>
> ④ `clientBean`은 prototypeBean의 `addCount()`를 호출해서 프로토타입 빈의 count를 증가.. count값이 1<br/>
> -&nbsp;클라이언트 B는 `clientBean`을 스프링 컨테이너에 요청해서 받는다. 싱글톤이므로 항상 같은 `clientBean`이 반환된다.<br/>
> -&nbsp;★<b>clientBean이 내부에 가지고 있는 프로토타입 빈은 이미 과거에 주입이 끝난 빈.<br/> 주입 시점에 스프링 컨테이너에 요청해서 프로토타입 빈이 새로 생성이 된 것이지, 사용할 때마다 새로 생성되는 것은 X</b><br/>
> ⑤ 클라이언트 B는 `clientBean.logic()`을 호출<br/>
> ⑥ `clientBean`은 prototypeBean의 `addCount()`를 호출해서 프로토타입 빈의 count를 증가한다. 
원래 count 값이 1이었으므로 2가 된다.<br/>

<br/>

### ■ 프로토타입 스코프 - 싱글톤 빈과 함께 사용시 Provider로 문제 해결
> 가장 간단한 방법은 싱글톤 빈이 프로토타입을 사용할 때 마다 스프링 컨테이너에 새로 요청하는 것

<br/>

#### &nbsp;● ObjectFactory, ObjectProvider
```
[ 특징 ]
- ObjectFactory: 기능이 단순, 별도의 라이브러리 필요 없음, 스프링에 의존
- ObjectProvider: ObjectFactory 상속, 옵션, 스트림 처리 등 편의 기능이 많고 별도의 라이브러리 필요없음.. 스프링에 의존
```

<br/>

#### &nbsp;● JSR-330 Provider
> 스프링부트 3.0 미만
>> `javax.inject:javax.inject:1` 라이브러리를 gradle에 추가해서 사용

<br/>

> 스프링부트 3.0 이상
>> `jakarta.inject:jakarta.inject-api:2.0.1` 라이브러리를 gradle에 추가해서 사용

<br/>

```
[ 특징 ]
- get() 메서드 하나로 기능이 매우 단순
- 별도의 라이브러리가 필요
- 자바 표준이므로 스프링이 아닌 다른 컨테이너에서도 사용가능
```

<br/>

### ■ 웹 스코프

<br/>

### &nbsp;● 웹 스코프의 특징
> -&nbsp;웹 스코프는 웹 환경에서만 동작<br/>
> -&nbsp;웹 스코프는 프로토타입과 다르게 스프링이 해당 스코프의 종료시점까지 관리하기 때문에 종료 메서드가
호출된다

<br/>

### &nbsp;● 웹 스코프의 종류
> -<b>request</b>: HTTP 요청 하나가 들어오고 나갈 때 까지 유지되는 스코프.. 각각의 HTTP 요청마다 별도의 빈 인스턴스가 생성되고 관리된다.<br/>
> -<b>session</b>: HTTP Session과 동일한 생명주기를 가지는 스코프<br/>
> -<b>application</b>: 서블릿 컨텍스트(`ServletContext`)와 동일한 생명주기를 가지는 스코프<br/>
> -<b>websicjet</b>: 웹 소켓과 동일한 생명주기를 가지는 스코프

<br/>

### ■ 스코프와 Provider
- `ObjectProvider`를 사용하여 `ObjectProvider.getObject()` 를 호출하는 시점까지 request scope 빈의
<b>생성을 지연</b>할 수 있다.
- `ObjectProvider.getObject()`를 <b>호출</b>하시는 시점에는 HTTP 요청이 진행중이므로 request scope 
빈의 생성이 정상 처리된다.

<br/>

### ■ 스코프와 프록시
```
@Component
@Scope(value = "request", proxyMode = ScopedProxyMode.TARGET_CLASS)
public class MyLogger {
}
```
&nbsp;-&nbsp;`proxyMode = ScopedProxyMode.TARGET_CLASS`를 추가<br/>
&nbsp;&nbsp;→ 적용 대상이 인터페이스가 아닌 클래스면 `TARGET_CLASS`를 선택<br/>
&nbsp;&nbsp;→ 적용 대상이 인터페이스면 `INTERFACES`를 선택

<br/>

### &nbsp;● 웹 스코프와 프록시 동작 원리
> *&nbsp;<b>CGLIB라는 라이브러리로 내 클래스를 상속 받은 가짜 프록시 객체를 만들어서 주입</b><br/>
> -&nbsp;`@Scope`의 `proxyMode = ScopedProxyMode.TARGET_CLASS)`를 설정하면 스프링 컨테이너는 CGLIB라는 바이트코드를 조작하는 라이브러리를 사용해서<br/> &nbsp;&nbsp;MyLogger를 상속받은 가짜 프록시 객체를 생성

<br/>

```
 ✔ 동작 정리
  - CGLIB라는 라이브러리로 내 클래스를 상속 받은 가짜 프록시 객체를 만들어서 주입
  - 가짜 프록시 객체는 실제 요청이 오면 그때 내부에서 실제 빈을 요청하는 위임 로직이 들어있다.
  - 가짜 프록시 객체는 실제 request scope와는 관계가 없다.. 가짜이고, 내부에 단순한 위임 로직만 있다.(싱글톤처럼 동작)
```
   
<br/>

```
 ✔ 특징 정리
  - 프록시 객체 덕분에 클라이언트는 마치 싱글톤 빈을 사용하듯이 편리하게 request scope를 사용할 수 있다.
  - 애노테이션 설정 변경만으로 원본 객체를 프록시 객체로 대체할 수 있다. → 다형성과 DI 컨테이너가 가진 큰 강점
  - 꼭 웹 스코프가 아니어도 프록시는 사용할 수 있다.
```
   
<br/>

❗주의점
> 마치 싱글톤을 사용하는 것 같지만 다르게 동작하기 때문에 주의해서 사용해야 한다.<br/>
> scope는 꼭 필요한 곳에만 최소화해서 사용.. 무분별하게 사용하면 유지보수하기 어려워진다.

<br/>