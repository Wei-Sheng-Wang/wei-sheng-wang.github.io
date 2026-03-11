---
title: "SOLID Principles"
date: 2025-01-20
description: "An introduction to SOLID Principles"
tags: ["SOLID", "software engineering", "design patterns", "programming", "OOP"]
categories: ["general"]
---

## What is SOLID?
SOLID is a set of principles that help you write better code. It stands for

1. Single Responsibility Principle
2. Open/Closed Principle 
3. Liskov Substitution Principle
4. Interface Segregation Principle
5. Dependency Inversion Principle

## Single Responsibility Principle (SRP)
SRP states that a class or module should only have one reason to change. This means that a class should only focus on a single well-define task or responsibility. You can think of 'responsibility' as the axis of change in your software. If you have more than one reason why your class needs to be modified, you likely have violated SRP.


To better grasp this concept, imagine a Swiss Army knife and a screw driver. The Swiss Army knife has a blade, a screw driver, a bottle opener, a can opener, etc. It's convenient for relatively small tasks, but if you need to do some serious work, you'd probably reach out for a dedicated screw driver.

```cpp
#include <string>

class User {
public:
    User(std::string name, std::string email, std::string password)
        : name_(name), email_(email), password_(password) {}


    void saveToDatabase() {
        // save user to database
    }

    void sendEmail() {
        // send email to user
    }

    void generateUserProfile() {
        // print user name, email, password
    }
private:
    std::string name_;
    std::string email_;
    std::string password_;

};
```

As you can see above, the `User` class has three responsibilities:
1. Save user to database
2. Send email to user
3. Generate user profile


If you need to change the database schema, the email sending logic, or how the user profile is generated, you need to modify the `User` class. This violates SRP.

To fix this, we can split the `User` class into 3 separate classes:

```cpp
class User {
public:
    User(std::string name, std::string email, std::string password)
        : name_(name), email_(email), password_(password) {}

}

class UserDatabase {
public:
    void saveToDatabase(User user) {
        // save user to database
    }
}

class UserEmail {
public:
    void sendEmail(User user) {
        // send email to user
    }
}

class UserProfile {
public:
    void generateUserProfile(User user) {
        // print user name, email, password
    }
}
```

Why is SRP important?

1. **Improved maintainability** - Changes in one part of the system is less likely to adversely affect other parts.
2. **Easier to understand** - Smaller focused classes are easier to understand and reason about.
3. **Enhanced reusability** - Classes that have only one responsibility are easier to be reused in different parts of the system.
4. **Testability** - Focused classes are easier to test because they have fewer dependencies and are easier to isolate.

### Pitfalls of SRP

- **Over-engineering** - SRP is not a one size fits all solutions. Don't go overboard creating an excessive number of small classes. Evaluate your requirements and design and find a rightful balance.
- **Subjectivity** - Defining single responsbility is subject to interpretation. It depends on the context of your system and your expentations for future changes. This one takes experience and practice.

## Open/Cloased Principle (OCP)
The Open/Closed Principle states that software entities should be open for extension, but closed for modification. In other words, you should be able to add new features or functionalities wihout modifying existing code. Once the current code is tested and working, you should avoid changing it.

This might seem counterintuitive at first. How can you add additional features without modifying existing code? The key lies in polymorphism and abstraction.

Think of it like a LEGO set. Let's say you have built a LEGO house, and you want to add a new window. You don't take apart the entire house to add a window, you simply add new bricks to your creation. OCP encourages a similar approach to software design.

Imagine we have a simple `AreaCalculator` class that calculates the area of a shape.
```cpp
class Rectangle {
public:
    Rectangle(double width, double height)
        : width_(width), height_(height) {}

private:
    double width_;
    double height_;
};

class Circle {
public:
    Circle(double radius)
        : radius_(radius) {}

private:
    double radius_;
};


class AreaCalculator {
public:
    double calculateArea(Shape shape) {
        // shape is of type
        if()
    }
}
```
