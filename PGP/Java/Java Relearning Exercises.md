# Java Relearning Exercises

Use these to rebuild Java and OO fluency. Try each task in a small Java file and compile/run it.

## 1. Syntax Warm-Up

Write a class called `HelloWorld` with a `main` method that prints three lines:

```text
Hello Java
Classes contain code
main is static
```

Then modify it to print command-line arguments.

```java
public static void main(String[] args) {
    // print each argument with its index
}
```

## 2. Static Methods

Create a class `TextTools` with static methods:

```java
printMessage(String message)
repeat(String text, int n)
isLongerThan(String text, int limit)
```

Example behaviour:

```java
TextTools.repeat("ha", 3) // "hahaha"
TextTools.isLongerThan("hello", 3) // true
```

## 3. Basic Classes

Create a `Person` class with:

- private `name`;
- private `age`;
- constructor;
- getters;
- setter for age;
- method `describe()`.

Example:

```java
Person p = new Person("Alex", 19);
System.out.println(p.describe());
```

## 4. Constructors and `this`

Create a `Counter` class:

- private `value`;
- constructor taking initial value;
- `increment()`;
- `add(int n)`;
- `getValue()`.

Use `this.value` inside the constructor.

## 5. Static Data

Modify `Counter` so it also tracks how many `Counter` objects have been created.

```java
Counter a = new Counter(0);
Counter b = new Counter(10);
System.out.println(Counter.getCount()); // 2
```

## 6. Aggregation

Create a `Notebook` class that has an `ArrayList<String>` inside it.

Methods:

```java
addNote(String note)
getNoteCount()
getNote(int index)
printAll()
```

The point: `Notebook` hides the `ArrayList` and exposes notebook-specific behaviour.

## 7. Inheritance

Create:

```java
class Animal
class Bear extends Animal
class Fish extends Animal
```

Each animal should have:

```java
getName()
getNoise()
```

Then store them in an `Animal[]` and loop through them.

```java
Animal[] animals = { new Animal(), new Bear(), new Fish() };
for (Animal a : animals) {
    System.out.println(a.getName() + ": " + a.getNoise());
}
```

## 8. Interfaces

Replace the `Animal` superclass with an `Animal` interface.

```java
public interface Animal {
    String getName();
    String getNoise();
}
```

Make `Bear` and `Fish` implement it. Check that the loop still works.

## 9. Exceptions

Write a method:

```java
public static int safeDivide(int a, int b) throws ArithmeticException
```

If `b` is zero, throw an exception. Then call it inside a `try`/`catch`.

## 10. Collections

Create an `ArrayList<String>` of names.

Do the following:

- add five names;
- print them with a for-each loop;
- sort them using `Collections.sort`;
- reverse them using `Collections.reverse`;
- print again.

## 11. Generics

Create a generic `Box<T>` class.

```java
public class Box<T> {
    private T value;
}
```

Add:

```java
Box(T value)
T get()
void set(T value)
```

Test with `Box<String>` and `Box<Integer>`.

## 12. Iterators

Create a class `SimpleBag<T>` that stores items in an `ArrayList<T>` and implements `Iterable<T>`.

Minimum methods:

```java
add(T item)
iterator()
```

Then make this work:

```java
SimpleBag<String> bag = new SimpleBag<>();
bag.add("A");
bag.add("B");

for (String item : bag) {
    System.out.println(item);
}
```

## 13. Anonymous Classes

Write a tiny Swing program with a `JButton` and `JLabel`. Use an anonymous `ActionListener` so clicking the button changes the label.

Core idea:

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText("Clicked");
    }
});
```

## 14. Lambdas

Rewrite the previous exercise using a lambda.

```java
button.addActionListener(e -> label.setText("Clicked"));
```

## 15. Singleton

Implement this singleton:

```java
public class AppConfig {
    private static AppConfig oneObject = null;

    private AppConfig() { }

    public static AppConfig get() {
        // return the one shared object
    }
}
```

Add a field such as `themeName` and prove that two calls to `AppConfig.get()` return the same shared object.

## 16. Factory

Create an `AnimalFactory`.

```java
public class AnimalFactory {
    public Animal createBear() {
        return new Bear();
    }

    public Animal createFish() {
        return new Fish();
    }
}
```

Use the factory from `main` without directly calling `new Bear()` or `new Fish()` there.

## 17. Mini Exam-Style Questions

1. Explain the difference between a class and an object, using a Java example.

2. Explain the difference between `static` and instance methods.

3. Write a class that demonstrates encapsulation using private fields and public methods.

4. Explain the difference between aggregation and inheritance.

5. Given a superclass reference pointing to a subclass object, explain which overridden method runs and why.

6. Compare abstract classes and interfaces.

7. Explain why Java uses wrapper classes such as `Integer` with generics.

8. Explain how `ActionListener` demonstrates the Observer pattern.

9. Explain how `LayoutManager` demonstrates the Strategy pattern.

10. Explain when you would use a Factory instead of directly calling `new`.

## 18. Suggested Practice Loop

1. Write the smallest version that compiles.
2. Add fields and constructors.
3. Add methods one at a time.
4. Test from `main`.
5. Refactor fields to `private`.
6. Replace direct access with methods.
7. Look for whether the relationship is "has-a" or "is-a".

