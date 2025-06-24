# C++ Object-Oriented Programming Concepts

This document explains essential C++ OOP (Object-Oriented Programming) topics in detail, including Polymorphism, Aggregation, Association, Composition, Friend Class & Function, and Inheritance.

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

1. **Single**
2. **Multiple**
3. **Multilevel**
4. **Hierarchical**
5. **Hybrid**

### Access Specifiers:

* **Public**: Public and protected members stay accessible.
* **Protected**: Public becomes protected.
* **Private**: Everything becomes private.

### Conceptual Questions:

1. What is the purpose of inheritance in C++?
2. What are the different types of inheritance?
3. How does access specifier affect inheritance?
4. What is the Diamond Problem?
5. How do constructors behave in inheritance?

---

Thank You </>
