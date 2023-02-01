Dart - Class(2)
===
> ## ★ Cascade Operator
```dart
class Player { 
  String name;
  int xp;
  String team;

  Player({
    required this.name, 
    required this.xp, 
    required this.team,
    });

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var cong = Player(name: 'cong', xp: 1200, team: 'red');
  cong.name = 'las';
  cong.xp = 120000;
  cong.team = 'blue';
}
```

메인 함수는 아래와 같이 쓸 수 있다.
```dart
void main(){ 
  var cong = Player(name: 'cong', xp: 1200, team: 'red')
  ..name = 'las'
  ..xp = 120000
  ..team = 'blue'
  ..sayHello(); 
}
```
1. 생성자 생성 시 세미콜론 삭제
2. 생성자 이름 → '..'으로 변경
3. ★ class의 메소드도 호출 가능 
> ## ★ Enums 
### 오타로 인한 잘못된 데이터 사용 및 이슈 생성 방지를 위해 사용
### **사용 방법**
### 1. enum 선언 : 이때 값은 String(문자열)으로 적어줄 필요는 없다.  
```dart
enum Team {red, blue} 
enum XPLevel {beginner, medium, pro} 
```
### 2. enum class property에 적용
```dart
class Player { 
String name;
XPLevel xp;
Team team;
```
### 3. enum명.데이터 사용
```dart
  Player({
    required this.name, 
    required this.xp, 
    required this.team,
    });

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var cong = Player(name: 'cong', xp: XPLevel.beginner, team: Team.red,);
  var potato = cong
  ..name = 'las'
  ..xp = XPLevel.medium
  ..team = Team.blue;
}
```
> ## Abstract classes(추상화 클래스)
### 다른 클래스들이 어떤 청사진을 가지고 있어야 하는지 정의해주는 기능
### 1. abstract class 생성
```dart
abstract class Human {
  void walk();
}
```

### 2. abstract class 상속
```dart
class Player extends Human{ 
  String name;
  XPLevel xp;
  Team team;

  Player({
    required this.name, 
    required this.xp, 
    required this.team,
    });

  void sayHello() {
    print("Hi my name is $name");
  }

  void walk() {
    print("i'm walking");
  }
}
```
추상 클래스에 'walk'라는 메소드가 있기 때문에 생성해줌.   
즉, 추상 클래스는 특정 메소드를 생성하도록 하는 기능 존재.
> ## ★★★ Inheritance(상속)
### 1. class 생성
```dart
class Human { 
  final String name; 
  Human({required this.name}); 

  void sayHello() { 
    print("Hi my name is $name");
  }
}
```

### 2. class 상속 
```dart
enum Team {red, blue} 

class Player extends Human { 
  final Team team; 

  Player({
    required this.team,
    required String name, 
  }) : super(name:name); 
```
- 생성자 생성 시, Human 클래스에서 필수로 입력되어야 하는 name property를 required로 선언하여 값을 받아옴.   
- 콜론(:) 뒤에 super(name:name) 입력  
→ Player 생성자에 입력된 정보를 Human 클래스의 name property에도 전달  
→ Human 클래스의 생성자(**_Human({required this.name})_**)도 호출한다.

```dart
  @override
  void sayHello(){
    super.sayHello();
    print("and I play for ${team}");
  }
}
```
- 부모 클래스에 있는 메소드를 자식 클래스에서 변경하여 사용하고 싶을 경우, override 사용  
> ## ★★★ Mixin
### 생성자가 없는 클래스
- 클래스에 property를 추가할 때 주로 사용
- 해당 클래스의 내부 메소드 및 객체 호출 기능

 1. 클래스 생성
```dart
class Strong {
  final double strengthLevel = 1500.99;
}

class QuickRunner {
  void runQuick(){
    print("runnnnnnnn!");
  }  
}

class Tall {
  final double height = 1.99;
}

```
2. 다른 클래스에서 사용 (여러 클래스에 재사용 가능 ★  )
```dart
class Player with Strong, QuickRunner, Tall {}

class Horse with Strong, QuickRunner {}

class Kid with QuickRunner{}
```
- ### **상속(Inheritance) VS Mixin** 

|특징|상속|Mixin|
|:------:|:---:|:---:|
|사용 키워드|extends|with|
|변경 유무|부모 클래스에 접근해(super) 메소드 및 객체 변경 가능|변경 불가능|
|생성자 유무|○|Ｘ|


