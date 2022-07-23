## What is Object Oriented Programming?

Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects. There are many object-oriented programming languages including JavaScript, C++, Java, and Python.


## what is class

A class is an abstract blueprint used to create more specific, concrete objects. Classes often represent broad categories, like Car or Dog that share attributes. These classes define what attributes an instance of this type will have, like color, but not the value of those attributes for a specific object.

Classes can also contain functions, called methods available only to objects of that type. These functions are defined within the class and perform some action helpful to that specific type of object.

![image](https://www.devopsschool.com/blog/wp-content/uploads/2021/05/image-60.png)

```java
class Student{
    //Data member or attribute
    String name;
    String address;
    int age;

    //Memeber function
    void display_student()
    {
        System.out.println("name is - "+name);
    }
}
```