# C++ Object-Oriented Programming Concepts

This document explains essential C++ OOP (Object-Oriented Programming) topics in detail, including Polymorphism, Aggregation, Association, Composition, Friend Class & Function, and Inheritance.

---

## 📚 Table of Contents

1. [Polymorphism](#1-polymorphism)
2. [Aggregation](#2-aggregation)
3. [Association](#3-association)
4. [Composition](#4-composition)
5. [Friend Class and Friend Function](#5-friend-class-and-friend-function)
6. [Inheritance](#6-inheritance)
7. [Quic Quiz](#7-quik-quiz)

---

## 1. Polymorphism

Polymorphism means "many forms". It allows us to perform a single action in different ways. In C++, it is of two types:

### Types of Polymorphism:

1. **Compile-time (Static) Polymorphism**

   * Achieved through function overloading and operator overloading.
   * Decision is made during compile-time.

   ```cpp
   class Print {
   public:
       void show(int i) {
           cout << "Integer: " << i << endl;
       }
       void show(double d) {
           cout << "Double: " << d << endl;
       }
   };
   ```

2. **Runtime (Dynamic) Polymorphism**

   * Achieved through virtual functions.
   * Uses pointers or references to base class.
   * Decision is made at runtime.

   ```cpp
   class Base {
   public:
       virtual void show() {
           cout << "Base class" << endl;
       }
   };

   class Derived : public Base {
   public:
       void show() override {
           cout << "Derived class" << endl;
       }
   };
   ```

### Key Concepts:

* Virtual functions must be accessed through pointers/references.
* Use `override` keyword for clarity and safety.
* Abstract classes contain at least one pure virtual function.
* `final` can prevent overriding.

### Conceptual Questions:

1. What is the difference between static and dynamic polymorphism?
2. How does function overloading support polymorphism?
3. What is the role of virtual functions in polymorphism?
4. Can constructors be overloaded?
5. What is the advantage of runtime polymorphism?

---

## 2. Aggregation

Aggregation is a special form of association. It represents a "Has-A" relationship, where the contained object can exist independently of the container.

### Example:

```cpp
class Engine {
public:
    void start() {
        cout << "Engine Started" << endl;
    }
};

class Car {
private:
    Engine* engine;
public:
    Car(Engine* e) : engine(e) {}
    void start() {
        engine->start();
    }
};
```

### Key Points:

* Weak relationship.
* Lifetimes are independent.
* Aggregated objects are passed by reference or pointer.
* Used when multiple objects can share a single instance.

### Conceptual Questions:

1. What is aggregation in C++?
2. How is aggregation different from composition?
3. Does aggregation support shared ownership?
4. Can aggregated objects be reused elsewhere?
5. Is the destructor of the aggregated class responsible for deleting the component?

---

## 3. Association

Association defines a relationship between two classes that is not necessarily ownership.

### Example:

```cpp
class Teacher {
public:
    string name;
};

class Student {
public:
    string name;
    Teacher* teacher;
};
```

### Types of Association:

* One-to-One
* One-to-Many
* Many-to-One
* Many-to-Many

### Key Points:

* Bidirectional or unidirectional.
* No lifecycle dependency.
* Used for communication without ownership.

### Conceptual Questions:

1. What is an association in OOP?
2. How is association different from aggregation?
3. Can association be bidirectional?
4. What are different multiplicities in association?
5. Does association imply ownership?

---

## 4. Composition

Composition is a strong form of aggregation. It implies ownership and a strong lifecycle dependency.

### Example:

```cpp
class Heart {
public:
    Heart() { cout << "Heart Created" << endl; }
    ~Heart() { cout << "Heart Destroyed" << endl; }
};

class Human {
private:
    Heart heart;
public:
    Human() {}
};
```

### Key Points:

* Strong relationship.
* Lifetimes are bound together.
* Cannot exist without each other.
* The containing class manages the lifetime of the contained object.

### Conceptual Questions:

1. What is composition in C++?
2. How is composition implemented in code?
3. What happens when the containing object is destroyed?
4. Can the contained object be shared with others?
5. How is composition stronger than aggregation?

---

## 5. Friend Class and Friend Function

### Friend Function:

Allows a non-member function to access private/protected members of a class.

```cpp
class Box {
private:
    int width;
public:
    Box() : width(0) {}
    friend void printWidth(Box);
};

void printWidth(Box b) {
    cout << "Width: " << b.width << endl;
}
```

### Friend Class:

Allows all methods of another class to access private/protected members.

```cpp
class A;

class B {
public:
    void show(A&);
};

class A {
private:
    int x = 5;
    friend class B;
};

void B::show(A& obj) {
    cout << "A's private value: " << obj.x << endl;
}
```

### Key Points:

* Useful when two or more classes need to work very closely.
* Not inherited.
* Friendship is not mutual.

### Conceptual Questions:

1. What is a friend function?
2. What are the advantages of friend classes?
3. Can a friend function be a member of another class?
4. Does friendship violate encapsulation?
5. Is friendship reciprocal or inherited?

---

## 6. Inheritance

Inheritance allows one class to acquire the properties and behavior of another.

### Syntax:

```cpp
class Base {
public:
    void show() {
        cout << "Base" << endl;
    }
};

class Derived : public Base {
public:
    void display() {
        cout << "Derived" << endl;
    }
};
```

### Types of Inheritance:

1. **Single** - One base, one derived class.
2. **Multiple** - Multiple base classes.
3. **Multilevel** - Derived from a derived class.
4. **Hierarchical** - One base, multiple derived classes.
5. **Hybrid** - Combination of above types.

### Access Specifiers:

* **Public**: Public and protected members stay accessible.
* **Protected**: Public becomes protected.
* **Private**: Everything becomes private.

### Key Points:

* Constructors of base are called before derived.
* Destructors are called in reverse order.
* Virtual inheritance prevents Diamond Problem.

### Conceptual Questions:

1. What is the purpose of inheritance in C++?
2. What are the different types of inheritance?
3. How does access specifier affect inheritance?
4. What is the Diamond Problem?
5. How do constructors behave in inheritance?

---

Here are **code-based conceptual questions only**, organized by topic:

# Quik Quiz
---

### 🔁 **Polymorphism**

1. What will be the output of this code using a base class pointer to call a derived class method?
2. Is function overloading an example of compile-time or runtime polymorphism?
3. What happens if you remove the `virtual` keyword in a polymorphic base class function?
4. Can constructors be virtual in C++? Why or why not?
5. What does the `override` keyword do, and what happens if it's omitted?

---

### 🧩 **Aggregation**

6. If an object is passed into a constructor by pointer, does that indicate aggregation or composition?
7. What happens to the aggregated object when the container object is destroyed?
8. Can multiple container objects share the same aggregated object? Why?
9. Does aggregation imply memory management responsibility?
10. How would you identify aggregation by just looking at the code?

---

### 🔗 **Association**

11. Can an associated object exist without the class it's linked to?
12. Is this a one-to-one, one-to-many, or many-to-many association?
13. What kind of relationship exists if two classes just reference each other?
14. How does association differ from inheritance in C++?
15. Can association exist without pointers or references?

---

### 🧱 **Composition**

16. What is the order of constructor and destructor calls in a composed class?
17. Can you reuse a composed object across multiple container classes?
18. How does the destruction of a container class affect its composed members?
19. Does composition imply strong or weak coupling?
20. In what scenario would you prefer composition over inheritance?

---

### 🧑‍🤝‍🧑 **Friend Class & Function**

21. Can a friend function access private data members of a class?
22. Is friendship reciprocal between classes?
23. Can a friend function be a member of another class?
24. What are the security implications of using friend functions?
25. Does declaring a friend class break encapsulation? Why or why not?

---

### 🧬 **Inheritance**

26. What is the output if both base and derived classes define the same function without `virtual`?
27. How does the constructor call order work in inheritance?
28. What is the purpose of the `protected` access modifier in inheritance?
29. What problem does virtual inheritance solve?
30. Can a derived class inherit private members from a base class? How?

---



## Thank You!
