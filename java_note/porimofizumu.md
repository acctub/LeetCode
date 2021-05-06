---
description: 多態性、多様性（同じ記述で様々な処理を切り替えることができる）
---

# ポリモフィズム

スーパークラスのメソッドがサブクラスでオーバライドされている場合、スーパークラス型の変数からメソッドを実行しても、サブクラスのメソッドの実行結果になります。その実用例は以下：

```java
class Main {

  public static void main(String[] args) {
    String type = args[0];
    PoCalcBaseSample calc = null;
    if (type.equals("1")) {
      calc = new PoAddSample();
    } else if (type.equals("2")) {
      calc = new PoSubSample();
    }
    calc.num1 = 9;
    calc.num2 = 3;
    int answer = calc.calc();
    System.out.println("計算結果は" + answer + "です");

  }
}

class PoCalcBaseSample {
    int num1 = 0;
    int num2 = 0;
    int calc() {
        return 0;
    }
}
class PoAddSample extends PoCalcBaseSample {
    int calc() {
        return num1 + num2;
    }
}
class PoSubSample extends PoCalcBaseSample {
    int calc() {
        return num1 - num2;
    }
}

```

#### アップキャストとダウンキャスト

 スーパークラスの型へサブクラスのインスタンスを代入することを**アップキャスト**と呼びます。アップキャストをしても、そのインスタンスの実体はサブクラスのインスタンスのままなので、元のサブクラスの変数に代入して戻すことができます。これを**ダウンキャスト**と呼びます。

```java
class Animal{}
class Cat extends Animal {}
class Dog extends Animal {}

class Main {
    public static void main(String[] args) {
        Dog obj1 = new Dog();
        Animal obj2 = obj1;     // アップキャスト
        Dog obj3 = (Dog)obj2;   // ダウンキャスト（理論上可能）
      	Dog obj3 = obj2;   // エラー（だけと危ないので手動にする必要がある）
    }
}
```

