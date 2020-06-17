# Spring

> 학습 목표 - Spring 기본적인 개념과 동작 원리를 이해한다.

### Framework 란?

- Framework는 개발자에게 애플리케이션을 개발하는데 있어 필요한 구조화된 기본 뻐대를 제공함으로써 애플리케이션의 기본 구조를 정하고 이 구조 위에서 코드를 작성하게 함으로써 개발에 있어 생산성을 높여준다.
- Spring 역시 Framework의 한 종류로서 **DI** 를 사용하여 디자인 패턴에 대한 자세한 이해없이도 객체를 효율적으로 사용 가능하게끔 해준다. - 객체를 **Singleton Pattern** 으로 사용 가능
  - Singleton Pattern : 객체의 인스턴스가 단 하나뿐인 특별한 객체, 어디서든 접근이 가능하다.

</br>

### Spring Container

- Spring 은 Spring Container라는 Runtime Engine을 제공하며, 해당 컨테이너를 통해 객체의 생성부터 소멸까지의 **Life Cycle** 을 관리한다.
- 해당 과정의 관리를 위해 **IoC**와 **DI** 가 사용된다.

</br>

### IoC - Inversion of Control (제어반전)

- IoC는 Inversion of Control의 약자로, 말 그대로 프로그램의 제어 흐름의 구조가 바뀌는 것을 의미한다.
- IoC를 통하여 객체의 권한이 Spring Container에 존재할 수 있게 된다. 이로인해, 일반적으로 Spring 내부에서 일반적인 흐름과 다르게 객체가 언제 생성되고 사용되는지 알 수 없다.
- IoC의 사용을 통해서 애플리케이션 설계가 깔끔해지며, 유연성과 확장성이 증가한다.

</br>

### DI - Dependency Injection (의존성 주입)

- to be continue...

