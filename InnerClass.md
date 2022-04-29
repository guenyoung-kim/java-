# Inner Class

### 왜 사용하는가?
내부클래스란 간단히 말해서 어떤 클래스 내에서 생성된 클래스를 의미한다.

내부클래스를 사용하는 이유는 클래스내에 소스코드를 좀 더 효율적으로 관리하고 조직화하기 위해 사용하는데

예를들어 같은 성격을 요구하는 VO가 있지만 해당 VO의 필드가 분리될 필요성이 있을 때 개별적인 VO 클래스를 따로 생성하는 것보다

하나의 성격을 공유하는 클래스를 생성 후 내부클래스를 통해 구분지을 수 있다.

### 내부클래스의 구분
Inner Class는 정의되는 위치에 따라 Member Class와 Local Class로 구분지어진다.

Member Class 

* 멤버변수와 동일한 위치에 선언된 내부클래스를 의미.
* static과 instance로 나눠짐.
* 외부에서도 사용할 때 멤버클래스를 사용.
* 멤버변수와 성격이 유사.

Local Class

* 메서드 내에 클래스가 선언된 내부클래스를 의미.
* Local Class와 Anonymous Class로 나눠짐.
* 활용범위가 메소드블록 내부에서 사용되는 등 제한할 때 사용.
* 지역변수와 성격이 유사.

### 내부클래스의 사용
#### Instance Member Class
내부클래스의 객체생성을 위해 외부클래스가 필요

```
class Outside {        // 외부 클래스 (=Top Level Class)
    public class Inside {        // 내부 클래스 (일반 멤버 변수와 동일한 위치)
        // ...
    }
}
 
public class InnerClass {
    public static void main(String args[]) {
        Outside outer = new Outside();    // 내부 클래스의 객체 생성을 위해 외부 클래스 객체 생성
        Outside.Inside inner = outer.new Inside();
    }
}
```
#### Static Member Class
외부클래스의 객체를 생성하지 않아도 내부클래스 생성가능

```
class Outside {        // 외부 클래스 (=Top Level Class)
    public static class StaticInside {        // static 내부 클래스
        // ...
    }
}
 
public class InnerClass {
    public static void main(String args[]) {
        Outside.StaticInside sinner = new Outside.StaticInside();
    }
}
```

#### Local Class
메소드 내에서 선언된 내부클래스로 메소드 내에서만 생성가능

```
public class InnerClass {
    public void method() {
        class Inner{
            public void print() {
                System.out.println("Local Class");
            }
        }

        Inner inner = new Inner();
        inner.print();
    }

    public static void main(String[] args) {
        InnerClass innerClass = new InnerClass();
        innerClass.method();
    }
}
```

#### Anonymous Class





출처: https://data-make.tistory.com/213 [Data Makes Our Future]
