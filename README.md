# 미션 목표

- OOP 첫걸음 내딛기
- MVC 패턴
- Java Collection
- 불변객체

# 최소 리뷰 횟수 - 3회

### 기능 목록을 반드시 README.md에 작성한다.

## 🚀 기능 요구사항

> 원본출처 : [https://github.com/woowacourse/java-racingcar-precourse](https://github.com/woowacourse/java-racingcar-precourse)
>

초간단 자동차 경주 게임을 구현한다.

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`를 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
- 아래의 프로그래밍 실행 결과 예시와 동일하게 입력과 출력이 이루어져야 한다.

## ✍🏻 입출력 요구사항

### ⌨️ 입력

- 경주 할 자동차 이름(이름은 쉼표(,) 기준으로 구분)

```java
pobi,woni,jun
```

- 시도할 회수

```java
5
```

### 🖥 출력

- 각 차수별 실행 결과

```java
pobi : --
woni : ----
jun : ---
```

- 단독 우승자 안내 문구

```java
최종 우승자 : pobi
```

- 공동 우승자 안내 문구

```java
최종 우승자 : pobi, jun
```

- 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 [ERROR] 로 시작해야 한다.

```java
[ERROR] 시도 횟수는 숫자여야 한다.
```

### 💻 프로그래밍 실행 결과 예시

```java
경주할 자동차 이름을 입력하세요.(이름은 쉼표(,) 기준으로 구분)
pobi,woni,jun
시도할 회수는 몇회인가요?
5

실행 결과
pobi : -
woni : 
jun : -

pobi : --
woni : -
jun : --

pobi : ---
woni : --
jun : ---

pobi : ----
woni : ---
jun : ----

pobi : -----
woni : ----
jun : -----

최종 우승자 : pobi, jun
```

## 🎱 프로그래밍 요구사항

- 프로그램을 실행하는 시작점은 `Application`의 `main()`이다.
- JDK 11 버전에서 실행 가능해야 한다.
- 자바 코드 컨벤션을 지키면서 프로그래밍한다.
    - [https://naver.github.io/hackday-conventions-java](https://naver.github.io/hackday-conventions-java)
- indent(인덴트, 들여쓰기) `depth를 1`이 넘지 않도록 구현한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메소드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- `함수(또는 메소드)가 한 가지 일만 하도록 최대한 작게` 만들어라.
- 프로그래밍 요구사항에서 별도로 변경 불가 안내가 없는 경우 파일 수정과 패키지 이동을 자유롭게 할 수 있다.

### 추가된 요구사항

- 함수(또는 메소드)의 길이가 10라인을 넘어가지 않도록 구현한다.
    - 함수(또는 메소드)가 한 가지 일만 잘 하도록 구현한다.
- else 예약어를 쓰지 않는다.
    - 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
    - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.

### 프로그래밍 요구사항 - Car 객체

- 다음 Car 객체를 활용해 구현해야 한다.
- Car 기본 생성자를 추가할 수 없다.
- name, position 변수의 접근 제어자인 private을 변경할 수 없다.
- 가능하면 setPosition(int position) 메소드를 추가하지 않고 구현한다.

```java
public class Car {
    private final String name;
    private int position = 0;

    public Car(String name) {
        this.name = name;
    }

    // 추가 기능 구현
}
```

### 기능 목록 (2023.1.13)
1. 입력메세지를 출력한다. (CarInput, View)
경주할 자동차 이름을 입력하세요.(이름은 쉼표(,) 기준으로 구분)

2. 경주할 자동차를 입력받는다.

3. 자동차의 이름이 모두 5자 이하인지 확인한다. (CarCheck, Model)
3-1. 아니라면 오류를 발생시키고 1부터 반복한다. (CarInput, View)
3-2. 맞다면 입력받은 자동차를 쉼표를 기준으로 리스트에 저장한다.

4. 입력메세지를 출력한다. (NumberInput, View)
시도할 회수는 몇회인가요?

5. 시도할 회수를 입력 받는다.

6. 입력이 0 이상의 정수인지 확인한다. (NumberCheck, Model)
6-1. 아니라면 오류를 발생시키고 5부터 반복한다. (NumberInput, View)

7. 입력받은 자동차들을 토대로 Car 클래스를 원소로 가지는 리스트를 생성한다. (CreateCarList, Model) 

8. 시도할 회수만큼 게임을 진행한다. (RacingCarGame, Controller)

9. 자동차 배열의 크기만큼의 리스트에 0~9사이의 난수를 저장한다. 

10. i번째에 저장한 난수의 크기가 4이상일 경우 전진 여부를 나타내는 boolean형 리스트의 i번째 원소를 true로 설정한다.

11. boolean형 리스트를 보고 i번째 차가 전진을 한다면 Car 클래스를 원소로 가지는 리스트의 i번째 원소의 position에 +1을 더해준다.

12. 실행결과를 출력한다.

13. 9부터 12까지 반복한다.

14. 가장 큰 값의 position을 구하고 출력해준다.
14-1. 여러 개라면 쉼표로 나누어 출력해준다.
