# SOLID Design Principles in java
## Introduction
  The SOLID principles are a set of five design principles that help developers create more maintainable, understandable, and flexible software. These principles are particularly useful in object-oriented programming and can significantly improve the quality of a codebase. This report outlines each of the SOLID principles, their importance, and provides Java code samples to illustrate their application.

---

### 1. Single Responsibility Principle (SRP)
* A class should have only one reason to change, meaning it should have only one job or responsibility.

* By adhering to SRP, we can create classes that are easier to understand and maintain. Changes in one part of the system are less likely to affect other parts.
* Example:
    ```java
    // Bad Example

    class Book {
        void printDetails() {
            System.out.println("Printing book details");
        }   
        void saveToFile() {
            System.out.println("Saving book to file");
        }
    }

    // Good Example

    class Book {
        void printDetails() {
            System.out.println("Printing book details");
        }
    }

    class FileManager {
        void saveToFile() {
            System.out.println("Saving book to file");
        }
    }
    ```

---

### 2. Open/Closed Principle (OCP)
* Software entities (classes, modules, functions) should be open for extension but closed for modification.
* New functionality can be added without altering existing code, minimizing the risk of introducing bugs.
* Example:
    ```java
    // Bad Example

    class Greeting {
        void greet(String language) {
            if (language.equals("English")) {
                System.out.println("Hello");
            } else if (language.equals("Telugu")) {
                System.out.println("Namaste");
            }
        }
    }

    // Good Example

    interface Greeting {
        void greet();
    }

    class EnglishGreeting implements Greeting {
        public void greet() {
            System.out.println("Hello");
        }
    }

    class TeluguGreeting implements Greeting {
        public void greet() {
            System.out.println("Namaste");
        }
    }


    ```

---

### 3. Liskov Substitution Principle (LSP)
* Subtypes should be substitutable for their base types without altering the correctness of the program.
* Ensures that derived classes extend behavior without changing the intended use of the base class.
* Example:
    ```java
    // Bad Example

    class Bird {
        void fly() {
            System.out.println("Bird is flying");
        }
    }

    class Penguin extends Bird {
        void fly() {
            throw new UnsupportedOperationException("Penguin can't fly");
        }
    }

    // Good Example

    interface Bird {
        void move();
    }

    class FlyingBird implements Bird {
        public void move() {
            System.out.println("Flying");
        }
    }

    class Penguin implements Bird {
        public void move() {
            System.out.println("Walking");
        }
    }

    ```

---

### 4. Interface Segregation Principle (ISP)
* A class should not be forced to implement interfaces it does not use. Instead, smaller, more specific interfaces are better.
* Promotes flexibility and minimizes the impact of changes in interfaces.
* Example:
    ```java
    // Bad Example

    interface Animal {
        void run();
        void swim();
    }

    class Dog implements Animal {
        public void run() {
            System.out.println("Dog is running");
        }

        public void swim() {
            System.out.println("Dog is swimming");
        }
    }

    class Fish implements Animal {
        public void run() {
            throw new UnsupportedOperationException("Fish can't run");
        }

        public void swim() {
            System.out.println("Fish is swimming");
        }
    }

    // Good Example

    interface Runnable {
        void run();
    }

    interface Swimmable {
        void swim();
    }

    class Dog implements Runnable, Swimmable {
        public void run() {
            System.out.println("Dog is running");
        }

        public void swim() {
            System.out.println("Dog is swimming");
        }
    }

    class Fish implements Swimmable {
        public void swim() {
            System.out.println("Fish is swimming");
        }
    }

    ```

---

### 5. Dependency Inversion Principle (DIP)
* High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details; details should depend on abstractions.
* Promotes loosely coupled systems and easier testing.
* Example:
    ```java
    // Bad Example

    class Fan {
        void start() {
            System.out.println("Fan started");
        }
    }

    class Switch {
        private Fan fan;

        Switch() {
            fan = new Fan();
        }

        void press() {
            fan.start();
        }
    }

    // Good Example

    interface Device {
        void start();
    }

    class Fan implements Device {
        public void start() {
            System.out.println("Fan started");
        }
    }

    class Switch {
        private Device device;

        Switch(Device device) {
            this.device = device;
        }

        void press() {
            device.start();
        }
    }

    ```

---

### References
* SOLID Principles from Youtube - [click here](https://www.youtube.com/playlist?list=PL6n9fhu94yhXjG1w2blMXUzyDrZ_eyOme)
* SOLID Principles from Website - [click here](https://www.digitalocean.com/community/conceptual-articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)
  