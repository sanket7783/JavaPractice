Sure! Here’s a **comprehensive guide** to the `static` keyword in Java with explanations and examples. 🚀

---

# **🔹 `static` Keyword in Java**
The `static` keyword in Java is used for **memory management** and allows variables, methods, blocks, and nested classes to be associated with the class rather than an instance.

---

## **📌 1. `static` Variables (Class Variables)**
A `static` variable is **shared among all objects** of the class. It is stored in the **method area** and belongs to the class, not an instance.

### ✅ **Example: Static Variable**
```java
class Employee {
    static int companyCode = 1001;  // Shared among all objects
    String name;

    Employee(String name) {
        this.name = name;
    }

    void show() {
        System.out.println("Employee: " + name + ", Company Code: " + companyCode);
    }
}

public class StaticExample {
    public static void main(String[] args) {
        Employee e1 = new Employee("Alice");
        Employee e2 = new Employee("Bob");

        e1.show();
        e2.show();

        // Updating static variable
        Employee.companyCode = 2002;

        e1.show();
        e2.show();
    }
}
```

### **📝 Output**
```
Employee: Alice, Company Code: 1001
Employee: Bob, Company Code: 1001
Employee: Alice, Company Code: 2002
Employee: Bob, Company Code: 2002
```

**✅ Key Points:**
- `static` variable is shared across all instances.
- If modified, the change reflects in all objects.

---

## **📌 2. `static` Methods**
A `static` method belongs to the class and can be called without creating an object.

### ✅ **Example: Static Method**
```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}

public class StaticMethodExample {
    public static void main(String[] args) {
        int result = MathUtil.square(5); // Calling without an object
        System.out.println("Square: " + result);
    }
}
```

### **📝 Output**
```
Square: 25
```

**✅ Key Points:**
- Can be called using **class name** (`MathUtil.square(5)`).
- **Cannot use `this` or `super`** inside a static method.
- Can only access **static variables/methods** directly.

---

## **📌 3. `static` Block**
A `static` block is used for **initializing static variables** and executes **before the `main()` method** when the class is loaded.

### ✅ **Example: Static Block**
```java
class StaticBlockExample {
    static {
        System.out.println("Static block executed first!");
    }

    public static void main(String[] args) {
        System.out.println("Main method executed");
    }
}
```

### **📝 Output**
```
Static block executed first!
Main method executed
```

**✅ Key Points:**
- Runs **only once** when the class is loaded.
- Used for **initializing static variables** or configurations.

---

## **📌 4. `static` Nested Class**
A **static nested class** is a class declared inside another class but **without** needing an outer class instance.

### ✅ **Example: Static Nested Class**
```java
class Outer {
    static class Inner {
        void show() {
            System.out.println("Inside static nested class");
        }
    }
}

public class StaticNestedClassExample {
    public static void main(String[] args) {
        Outer.Inner obj = new Outer.Inner(); // No need to create Outer class instance
        obj.show();
    }
}
```

### **📝 Output**
```
Inside static nested class
```

**✅ Key Points:**
- `static` nested class **cannot access non-static members** of the outer class.
- Used for **grouping helper classes** inside a main class.

---

## **📌 5. `static` Object Creation in Static Block**
You **can** create an object of the class inside a `static` block.

### ✅ **Example: Creating Object in Static Block**
```java
class Demo {
    static Demo obj;

    static {
        obj = new Demo(); // Creating an object in a static block
        System.out.println("Static block executed");
    }

    void show() {
        System.out.println("Inside show() method");
    }

    public static void main(String[] args) {
        obj.show();
    }
}
```

### **📝 Output**
```
Static block executed
Inside show() method
```

---

## **📌 6. Can We Override Static Methods?**
❌ **No, static methods cannot be overridden.**  
If a subclass defines a `static` method with the same signature as a superclass method, it is **method hiding, not overriding.**

### ❌ **Example: Method Hiding**
```java
class Parent {
    static void show() {
        System.out.println("Static method in Parent");
    }
}

class Child extends Parent {
    static void show() {  // This hides the Parent's show method, not overrides it
        System.out.println("Static method in Child");
    }
}

public class StaticOverrideExample {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show(); // Calls Parent's method (not overridden)
    }
}
```

### **📝 Output**
```
Static method in Parent
```

---

## **📌 7. When to Use `static`?**
| Feature | When to Use |
|---------|------------|
| `static` Variable | When the value **must be shared** across all objects (e.g., a company code). |
| `static` Method | When the method **does not depend on instance variables** (e.g., utility methods). |
| `static` Block | When initializing **static variables** before `main()` runs. |
| `static` Nested Class | When a **class does not need access to outer class instance variables**. |

---

## **🎯 Summary**
| Feature | Explanation |
|---------|------------|
| `static` Variable | Shared across all objects, belongs to class. |
| `static` Method | Can be called without creating an object, but can't access non-static members. |
| `static` Block | Executes once when class is loaded, used for initialization. |
| `static` Nested Class | Works like a normal class but does not require an instance of the outer class. |

---

### 🚀 **Final Thoughts**
The `static` keyword is powerful for **memory management and class-level behavior**. It should be used **wisely** in situations where a variable, method, or block must be associated with the class rather than an object.

Would you like a **real-world example** on how companies use `static`? 😊