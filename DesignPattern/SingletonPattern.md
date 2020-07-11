# Singleton Pattern

* **Singleton Pattern** 이란, 인스턴스가 프로그램 내에서 오직 하나만 생성되는 것을 보장하고, 프로그램 어디에서든 해당 인스턴스에 접근할 수 있도록 하는 디자인 패턴이다.

  > **단 하나의 인스턴스** 생성을 보장 </br>
  >
  > 이후 프로그램 내 어디서든 **최초 생성된 인스턴스 사용**을 보장

* Singleton Pattern **장단점**

  * **장점**

    > 단 하나의 인스턴스를 보장하기에 **메모리** 사용에 이점을 가짐 </br>
    >
    > 전역 인스턴스으로 사용되기 때문에 다른 객체들과의 **데이터 공유**가 쉽다 </br>
    >
    > 최초 생성이후 **객체 로딩 시간**이 현저하게 줄어 성능이 좋아진다.

  * **단점**

    > 싱글톤으로 구현된 인스턴스가 너무 많은 업무를 맡거나 데이터를 공유시 다른 객체들과의 **결합도**가 높아져 "**개방 - 폐쇄 원칙**"을 위배하게 된다. - **확장성**, **유지보수** 측면에서 불이익 </br>
    >
    > **Multi-Thread** 환경에서 취약점을 지님 - 한개 인스턴스 보장 및 공유 데이터 Write 업무 등

* 구현

  * Java

    ~~~java
    // Thread Safe Lazy Initialization
    public class SingletonClass {
      private static SingletonClass instance;
      
      // 단 하나의 인스턴스 생성을 위해 생성자를 private을 통해 숨기는 것
      // 다른 객체가 생성자를 임의로 사용할 수 없도록 하는 것
      private SingletonClass () {}
      
      // 멀티쓰레드 환경에서 단 하나의 인스턴스 생성을 보장하기 위한 동기화
      public static synchronized SingletonClass getInstance () {
        if (instance == null) {
          instance = new SingletonClass();
        }
        return instance;
      }
    }
    
    // Thread safe lazy initialization + Double Checked locking
    // 앞선 게으른 초기화 방식의 성능 저하를 완하
    public class SingletonClass {
      // volatile 메인 메모리부터 값을 읽어드릴 수 있도록 보장
      private volatile static SingletonClass instance;
      
      private SingletonClass () {}
      
      public static SingletonClass getInstance () {
        if (instance == null) {
          synchronized (SingletonClass.class) {
            if (instance == null) {
              instance = new SingletonClass();
            }
          }
        }
      }
    }
    
    // Initialization on demand holder idiom (내부 holder에 의한 초기화 방식)
    // Holder 방식은 JVM의 클래스 초기화 과정에서 보장되는 원자적 특성을 이용하여 싱글턴 초기화 문제에 대한 책임을 JVM에 떠넘긴다.
    // 가장 많이 쓰여지는 구현
    public class SingletonClass {
      
      private SingletonClass () {}
      
      // jVM의 클래스 로더 메커니즘과 클래스의 로드 시점을 이용하여 내부 클래스를 통해 생성 시킴으로써 쓰레드 간의 동기화 문제를 해결한다.
      // final 키워드를 통해 다시 변경이 될 수 없게 한다.
      private static class innerHolder () {
        private static final SingletonClass instance = new SingletonClass();
      }
      
      public static SingletonClass getInstance () {
        return InnerHolder.instance;
      }
    }
    ~~~

  * Python

    ```python
    
    ```

* 

