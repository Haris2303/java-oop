# Java Object Oriented Programming (OOP)

## Table Of Contents

- [Pengenalan OOP](#pengenalan-oop)
- [Class](#class)
- [Object](#object)
- [Attributes](#attributes)
- [Method](#method)
- [Constructor](#constructor)
- [Constructor Overloading](#constructor-overloading)
- [Variable Shadowing](#variable-shadowing)
- [This Keyword](#this-keyword)
- [Inheritance](#inheritance)
- [Method Overriding](#method-overriding)
- [Super Keyword](#super-keyword)
- [Super Constructor](super-constructor)
- [Polymorphism](#polymorphism)
- [Type Check dan Casts](#type-check-dan-casts)
- [Variable Hiding](#variable-hiding)
- [Package](#package)
- [Access Modifier](#access-modifier)
- [Import](#import)
- [Abstract Method](#abstract-method)
- [Getter dan Setter](#getter-dan-setter)
- [Interface](#interface)
- [Interface Inheritance](#interface-inheritance)
- [Default Method](#default-method)
- [toString Method](#tostring-method)
- [Equals Method](#equals-method)
- [HashCode Method](#hashcode-method)
- [Final Class](#final-class)
- [Final Method](#final-method)
- [Inner Class](#inner-class)
- [Anonymous-class](#anonymous-class)
- [Static Keyword](#static-keyword)
- [Record Class](#record-class)
- [Enum Class](#enum-class)
- [Exception](#exception)
- [Runtime Exception](#runtime-exception)
- [Error](#error)
- [Stack Trace Element Class](#stack-trace-element-class)
- [Try With Resource](#try-with-resource)
- [Annotation](#annotation)
- [Reflection](#reflection)

## Pengenalan OOP

**Apa itu Object Oriented Programming?**

- Object Oriented Programming adalah sudut pandang bahasa pemrograman yang berkonsep `objek`
- Ada banyak sudut pandang bahasa pemrograman, namun OOP adalah yang sangat populer saat ini.
- Ada beberapa istilah yang perlu dimengerti dalam OOP, yaitu: Object dan Class

**Apa itu Object?**

- Object adalah data yang berisi field / properties / attributes dan method / function / behavior
- Semua data bukan primitif di Java adalah object, dari mulai Integer, Boolean, Character, String dan yang lainnya

**Apa itu Class?**

- Class adalah blueprint, prototype atau cetakan untuk membuat Object
- Class berisikan deklarasi semua properties dan functions yang dimiliki oleh Object
- Setiap Object selalu dibuat dari Class
- Dan sebuah Class bisa membuat Object tanpa batas

## Class

**Membuat Class**

- Untuk membuat class, kita bisa menggunakan kata kunci class
- Penamaan class biasa menggunakan format `CamelCase`

Kode Pembuatan Class:

```java
class Person {
}
```

## Object

**Membuat Object**

- Object adalah hasil instansiasi dari sebuah class
- Untuk membuat object kita bisa menggunakan kata kunci `new`, dan diikuti dengan nama Class dan kurung ()

Kode Pembuatan Object:

```java
var person1 = new Person();
Person person2 = new Person();

Person person3;
person3 = new Person();
```

## Attributes

- Fields / Properties / Attributes adalah data yang bisa kita sisipkan di dalam Object
- Namun sebelum kita bisa memasukkan data di fields, kita harus mendeklarasikan data apa aja yang dimiliki object tersebut di dalam deklarasi class-nya
- Membuat field sama seperti membuat variable, namun ditempatkan di block class

Kode Pembuatan Attributes:

```java
class Person {
    String name;
    int age;
    final String gender = "Laki-laki";
}
```

**Manipulasi Attribute**

- Attributes yang ada di object, bisa kita manipulasi. Tergantung final atau bukan.
- Jika final, berarti kita tidak bisa mengubah data field nya, namun jika tidak, kita bisa mengubah field nya
- Untuk memanipulasi data field, sama seperti cara pada variable
- Untuk mengakses field, kita butuh kata kunci . (titik) setelah nama object dan diikuti nama fields nya

Kode Pembuatan Manipulasi Attribute:

```java
var person = new Person();
person.name = "Otong";
person.age = 17;
// person.gender = "Tidak bisa diubah";

System.out.println(person.name);
System.out.println(person.age);
System.out.println(person.gender);
```

## Method

- Selain menambahkan attribute, kita juga bisa menambahkan method ke object
- Cara dengan mendeklarasikan method tersebut di dalam block class
- Sama seperti method biasanya, kita juga bisa menambahkan return value, parameter dan method overloading di method yang ada di dalam block class
- Untuk mengakses method tersebut, kita bisa menggunakan tanda titik (.) dan diikuti dengan nama method nya. Sama seperti mengakses attribute

Kode Pembuatan Method (1):

```java
class Person {
    String name;
    int age;
    final String gender = "Laki-laki";

    void sayHello(String paramName) {
        System.out.printf("Hello %s, My Name is %s", paramName, name);
    }
}
```

Kode Pembuatan Method (2):

```java
var person = new Person();
person.name = "Otong Surotong";

person.sayHello("Ucup");
```

## Constructor

- Saat kita membuat Object, maka kita seperti memanggil sebuah method, karena kita menggunakan kurung ()
- Di dalam class Java, kita bisa membuat constructor, constructor adalah method yang akan dipanggil saat pertama kali Object dibuat.
- Mirip seperti di method, kita bisa memberi parameter pada constructor
- Nama constructor harus sama dengan nama class, dan tidak membutuhkan kata kunci void atau return value

Kode Pembuatan Constructor:

```java
class Person {
    String name;
    int age;
    final String gender = "Laki-laki";

    Person(String paramName, int paramAge) {
        name = paramName;
        age = paramAge;
    }

    void sayHello(String paramName) {
        System.out.printf("Hello %s, My Name is %s", paramName, name);
    }
}
```

Kode Penggunaan Constructor:

```java
var person = new Person("Ucup", 80);
person.name = "Ucup Surucup";

person.sayHello("Otong");
```

## Constructor Overloading

- Sama seperti di method, di constructor pun kita bisa melakukan overloading
- Kita bisa membuat constructor lebih dari satu, dengan syarat tipe data parameter harus berbeda, atau jumlah parameter harus berbeda

Kode Pembuatan Constructor Overloading:

```java
Person(String paramName, int paramAge) {
    name = paramName;
    age = paramAge;
}

Person(String paramName) {
    name = paramName;
}

Person() {

}
```

Kode Penggunaan Constructor:

```java
var person1 = new Person("Otong", 17);
var person2 = new Person("Ucup");
var person3 = new Person();
```

**Memanggil Constructor Lain**

- Constructor bisa memanggil constructor lain
- Hal ini memudahkan saat kita butuh menginisialisasi data dengan berbagai kemungkinan
- Cara untuk memanggil constructor lain, kita hanya perlu memanggilnya seperti memanggil method, namun dengan kata kunci this

Kode Memanggil Constructor Lain:

```java
Person(String paramName, int paramAge) {
    name = paramName;
    age = paramAge;
}

Person(String paramName) {
    this(paramName, null);
}

Person() {
    this(null);
}
```

## Variable Shadowing

- Variable shadowing adalah kejadian ketika kita membuat nama variable dengan nama yang sama di scope yang menutupi variable dengan nama yang sama di scope diatasnya
- Ini biasa terjadi seperti kita membuat nama parameter di method sama dengan nama field di class
- Saat terjadi variable shadowing, maka secara otomatis variable di scope diatasnya tidak bisa diakses

Kode Pembuatan Variable Shadowing:

```java
Person(String name, String age) {
    name = name; // attribute nama tidak berubah
    age = age; // attribute age tidak berubah
}

void sayHello(String name) {
    System.out.printf("Hello %s, My name is %s", name, name); // attribute name tidak diakses
}
```

## This Keyword

- Saat kita membuat kode di dalam block constructor atau method di dalam class, kita bisa menggunakan kata kunci this untuk mengakses object saat ini
- Misal kadang kita butuh mengakses sebuah field yang namanya sama dengan parameter method, hal ini tidak bisa dilakukan jika langsung menyebut nama field, kita bisa mengakses nama field tersebut dengan kata kunci this
- This juga tidak hanya digunakan untuk mengakses field milik object saat ini, namun juga bisa digunakan untuk mengakses method
- This bisa digunakan untuk mengatasi masalah variable shadowing

Kode This Keyword:

```java
Person(String name, int age) {
    this.name = name;
    this.age = age;
}

void sayHello() {
    this.sayHello("Otong");
}

void sayHello(String name) {
    System.out.printf("Hello %s, My name is %s", name, this.name);
}
```

## Inheritance

- Inheritance atau pewarisan adalah kemampuan untuk menurunkan sebuah class ke class lain
- Dalam artian, kita bisa membuat class Parent dan class Child
- Class Child, hanya bisa punya satu class Parent, namun satu class Parent bisa punya banyak class Child
- Saat sebuah class diturunkan, maka semua field dan method yang ada di class Parent, secara otomatis akan dimiliki oleh class Child
- Untuk melakukan pewarisan, di class child, kita harus menggunakan kata kunci extends lalu diikuti dengan nama class parent nya.

Kode Inheritance:

```java
class Manager {
    String name;

    void sayHello(String name) {
        System.out.printf("Hello %s, My name is %s", name, this.name)
    }
}

class VicePresident extends Manager {

}
```

Kode Mengakses Method Parent:

```java
var manager = new Manager();
manager.name = "Otong";
manager.sayHello("Ucup");

var vicePresident = new VicePresident();
vicePresident.name = "Bambang";
vicePresident.sayHello("Tutu");
```

## Method Overriding

- Method overriding adalah kemampuan mendeklarasikan ulang method di child class, yang sudah ada di parent class
- Saat kita melakukan proses overriding tersebut, secara otomatis ketika kita membuat object dari class child, method yang di class parent tidak bisa diakses lagi

Kode Method Overriding:

```java
class Manager {
    String name;

    void sayHello(String name) {
        System.out.printf("Hello %s, My name is %s", name, this.name)
    }
}

class VicePresident extends Manager {

    void sayHello(String name) {
        System.out.printf("Hello %s, My name is VP %s", name, this.name)
    }
}
```

Kode Mengakses Method Overriding:

```java
var manager = new Manager();
manager.name = "Otong";
manager.sayHello("Ucup");

var vicepresident = new VicePresident();
vicepresident.name = "Martin";
vicepresident.sayHello("Bambang");
```

## Super Keyword

- Kadang kita ingin mengakses method yang terdapat di class parent yang sudah terlanjur kita override di class child
- Untuk mengakses method milik class parent, kita bisa menggunakan kata kunci super
- Sederhananya, super digunakan untuk mengakses class parent
- Tidak hanya method, field milik parent class pun bisa kita akses menggunakan kata kunci super

Kode Super Keyword:

```java
class Shape {
    int getCorner() {
        return 0;
    }
}

class Rectangle extends Shape {
    int getCorner() {
        return 4;
    }

    int getParentCorner() {
        return super.getCorner();
    }
}
```

Kode Mengakses Super Keyword:

```java
var rectable = new Rectangle();

System.out.println(rectable.getCorner());
System.out.println(rectable.getParentCorner());
```

## Super Constructor

- Tidak hanya untuk mengakses method atau field yang ada di parent class, kata kunci super juga bisa digunakan untuk mengakses constructor
- Namun syaratnya untuk mengakses parent class constructor, kita harus mengaksesnya di dalam class child constructor
- Jika sebuah class parent tidak memiliki constructor yang tidak ada parameter-nya (tidak memiliki default constructor), maka class child wajib mengakses constructor class parent tersebut.

Kode Super Constructor:

```java
class Manager {
    String name;

    Manager(String name) {
        this.name = name;
    }

    void sayHello(String name) {
        System.out.printf("Hello %s, My name is Manager %s", name, this.name)
    }
}

class VicePresident extends Manager {

    VicePresident(String name) {
        super(name);
    }
}
```

Kode Menggunakan Super Constructor:

```java
var manager = new Manager("Otong");
manager.sayHello("Budi");

var vicePresident = new VicePresident("Yanto");
vicePresident.sayHello("Yanti");
```

## Object Class

- Di Java, setiap class yang kita buat secara otomatis adalah turunan dari class Object
- Walaupun tidak secara langsung kita eksplisit menyebutkan extends Object, tapi secara otomatis Java akan membuat class kita extends Object
- Bisa dikatakan class Object adalah superclass untuk semua class yang ada di Java

Kode Menggunakan Class Object:

```java
var manager = new Manager("Otong");
System.out.println(manager);
System.out.println(manager.toString());
```

## Polymorphism

- Polymorphism berasal dari bahasa Yunani yang berarti banyak bentuk
- Dalam OOP, Polymorphism adalah kemampuan sebuah object berubah bentuk menjadi bentuk lain
- Polymorphism erat hubungannya dengan Inheritance

Kode Inheritance:

```java
class Employee {
    String name;

    Employee(String name) {
        this.name = name;
    }
}

class Manager extends Employee {
    Manager(String name) {
        super(name);
    }
}

class VicePresident extends Manager {
    VicePresident(String name) {
        super();
    }
}
```

Kode Polymorphism:

```java
Employee employee = new Employee("Otong");
employee.sayHello("Budi");

employee = new Manager("Purnama");
employee.sayHello("Purnomo");

employee = new VicePresident("Martin");
employee.sayHello("Asep");
```

Kode Method Polymorphism:

```java
    sayHello(new Employee("Otong"));
    sayHello(new Manager("Ucup"));
    sayHello(new VicePresident("Budi"));
}

static void sayHello(Employee employee) {
    System.out.println("Hello " + employee.name);
}
```

## Type Check dan Casts

- Sebelumnya kita sudah tau cara melakukan konversi tipe data (casts) di tipe data primitif
- Casts juga bisa digunakan untuk tipe data bukan primitif
- Namun agar aman, sebelum melakukan casts, pastikan kita melakukan type check (pengecekan tipe data), dengan menggunakan kata kunci instanceof
- Hasil operator instanceof adalah boolean, true jika tipe data sesuai, false jika tidak sesuai

Kode Type Check dan Casts:

```java
static void sayHello(Employee employee) {
    if (employee instanceof VicePresident) {
        VicePresident vicePresident = (VicePresident) employee;
        System.out.println("Hello VP " + vicePresident.name);
    } else if (employee instanceof Manager) {
        Manager manager = (Manager) employee;
        System.out.println("Hello Manager " + manager.name);
    } else {
        System.out.println("Hello VP " + employee.name);
    }
}
```

## Variable Hiding

- Variable hiding merupakan masalah yang terjadi ketika kita membuat nama field sama di class child dengan nama field di class parent
- Tidak ada yang namanya field overriding, ketika kita buat ulang nama field di class class, itu berarti variable hiding
- Untuk mengatasi variable hiding, caranya kita bisa menggunakan super keyword
- Yang membedakan variable hiding dan method overriding adalah ketika sebuah object di casts
- Saat object di casts, method akan tetap mengakses method overriding, namun variable akan mengakses variable yang ada di class nya

Kode Variable Hiding:

```java
class Parent {
    String name;

    void doIt() {
        System.out.println("Do it from parent");
    }
}

class Child extends Parent {
    String name;

    void doIt() {
        System.out.println("Do it from child");
    }
}
```

Kode Variable Hiding vs Method Overriding:

```java
Child child = new Child();
child.name = "Martin";
chlid.doIt();
System.out.println(child.name);

Parent parent = (Parent) child;
parent.doIt();
System.out.println(parent.name);
```

## Package

- Saat kita membuat aplikasi, bisa dipastikan kita akan banyak sekali membuat class
- Jika class terlalu banyak, kadang akan menyulitkan kita untuk mencari atau mengklasifikasikan jenis-jenis class
- Java memiliki fitur package, yaitu fitur mirip folder / direktori, dimana kita bisa menyimpan class-class kita di dalam package
- Sama seperti folder / direktori, package juga bisa nested, kita bisa menggunakan tanda titik (.) untuk membuat nested package
- Ketika kita menyimpan class di dalam package, maka diatas file Java nya, kita wajib menyebutkan nama package nya

```java
package belajar.java.oop;

class Product {
    String name;
    int price;

    Product(String name, int price) {
        this.name = name;
        this.price = price;
    }
}
```

## Access Modifiers

- Access modifier adalah kemampuan membuat class, attribute, method dan constructor dapat diakses dari mana saja
- Sebelumnya teman-teman sudah melihat 2 access modifier, yaitu public dan default (no-modifier)
- Sekarang kita akan bahas access modifier lainnya

**Access Level**

| Modifier    | Class | Package | SubClass | World |
| ----------- | ----- | ------- | -------- | ----- |
| public      | Y     | Y       | Y        | Y     |
| protected   | Y     | Y       | Y        | N     |
| no modifier | Y     | Y       | N        | N     |
| private     | Y     | N       | N        | N     |

**Public Class**

- Saat kita membuat public class, kita hanya bisa membuat 1 public class di 1 file java
- Selain itu, nama public class harus sama dengan nama file

Kode Access Modifier (1):

```java
package belajar.java.oop;

public class Product {
    protected String name;
    protected int price;

    public String getName() {
        return name;
    }

    public int getPrice() {
        return price;
    }
}
```

Kode Access Modifier (2):

```java
package belajar.java.oop;

public class ProductApp {
    public static void main(String[] args) {
        Product product = new Product();
        product.name = "Indomie"; // bisa diakses karena di package yang sama
        product.price = 3000; // bisa diakses karena di package yang sama

        System.out.println(product.getName());
        system.out.println(product.getPrice());
    }
}
```

## Import

- Import adalah kemampuan untuk menggunakan class yang berada di package yang berbeda
- Syarat class yang bisa digunakan jika package nya berbeda adalah class yang harus public

Kode Import:

```java
package belajar.java.app;

import belajar.java.oop.Product;

public class ProductApp() {
    public static void main(String[] args) {
        Product product = new Product();
        product.name = "Indomie"; // error, beda package
        product.price = 2000; // error, beda package

        System.out.println(product.getName());
        System.out.println(product.getPrice());
    }
}
```

**Import Semua Package**

- Jika kita ingin mengimport semua class di dalam package, kita bisa menggunakan tanda `*`
- `import belajar.java.oop.*;`

**Default Import**

- Secara default, semua class yang ada di package `java.lang` sudah auto import, jadi kita tidak perlu melakukan import secara manual.
- Contoh class `String`, `Integer`, `Long`, `Boolean`, dan lain-lain terdapat di package `java.lang`. Oleh karena itu, kita tidak perlu meng-import nya secara manual

## Abstract Class

- Saat kita membuat class, kita bisa menjadikan sebuah class sebagai abstract class.
- Abstract class artinya, class tersebut tidak bisa dibuat sebagai object secara langsung, hanya bisa diturunkan
- Untuk membuat sebuah class menjadi abstract, kita bisa menggunakan kata kunci abstract sebelum kata kunci class
- Dengan demikian abstract class bisa kita gunakan sebagai kontrak untuk class child

Kode Abstract Class:

```java
// Location.java

package belajar.java.oop;

public abstract class Location {
    String name;
}
```

```java
// City.java

package belajar.java.oop;

public class City extends Location {

}
```

Kode Membuat Abstract Class:

```java
import belajar.java.oop.City;
import belajar.java.oop.Location;

public class AbstractClassApp {
    public static void main(String[] args) {
        var location = new Location(); // error
        var city = new City();
    }
}
```

## Abstract Method

- Saat kita membuat class yang abstract, kita bisa membuat abstract method juga di dalam class abstract tersebut
- Saat kita membuat sebuah abstract method, kita tidak boleh membuat block method untuk method tersebut
- Artinya, abstract method wajib di override di class child
- Abstract method tidak boleh memiliki access modifier private

```java
// Animal.java
public abstract class Animal {
    public string name;

    public abstract void run();
}
```

```java
// Cat.java

package belajar.java.oop;

public class Cat extends Animal {
    public void run() {
        System.out.println("Cat " + name + " is running");
    }
}
```

Kode Menggunakan Abstract Method:

```java
public class AbstractMethodApp {
    public static void main(String[] args) {
        Animal animal = new Cat();
        animal.name = "Eko";
        animal.run();
    }
}
```

## Getter dan Setter

**Encapsulation**

- Encapsulation artinya memastikan data sensitif sebuah object tersembunyi dari akses luar
- Hal ini bertujuan agar kita bisa menjaga agar data sebuah object tetap baik dan valid
- Untuk mencapai ini, biasanya kita akan membuat semua field menggunakan access modifier private, sehingga tidak bisa diakses atau diubah dari luar
- Agar bisa diubah, kita akan menyediakan method untuk mengubah dan mendapatkan field tersebut

**Getter dan Setter**

- Di Java, proses encapsulation sudah dibuat standarisasinya, dimana kita bisa menggunakan Getter dan Setter method.
- Getter adalah function yang dibuat untuk mengambil data field
- Setter ada function untuk mengubah data field

**Getter dan Setter Method**

| Tipe Data | Getter Method | Setter Method          |
| --------- | ------------- | ---------------------- |
| Boolean   | isXxx()       | setXxx(boolean value)  |
| primitif  | getXxx()      | setXxx(primitif value) |
| Object    | getXxx()      | setXxx(Object value)   |

Kode Getter dan Setter:

```java
public class Category {
    private String id;

    private boolean expensive;

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }
}
```

Kode Validation di Setter:

```java
public String getId() {
    return id;
}

public void setId(String id) {
    if(id != null) {
        this.id = id;
    }
}
```

## Interface

- Sebelumnya kita sudah tahu bahwa abstract class bisa kita gunakan sebagai kontrak untuk class child nya.
- Namun sebenarnya yang lebih tepat untuk kontrak adalah Interface
- Jangan salah sangka bahwa Interface disini bukanlah User Interface
- Interface mirip seperti abstract class, yang membedakan adalah di Interface, semua method otomatis abstract, tidak memiliki block
- Di interface kita tidak boleh memiliki field, kita hanya boleh memiliki constant (field yang tidak bisa diubah)
- Untuk mewariskan interface, kita tidak menggunakan kata kunci extends, melainkan implements

Kode Membuat Interface:

```java
// Car.java

package belajar.java.oop;

public interface Car {
    void drive();

    int getTire();
}
```

Kode Implementasi Interface:

```java
// Avanza.java

package belajar.java.oop;

public class Avanza implements Car {
    public void drive() {
        System.out.println("Drive Avanza");
    }

    public int getTire() {
        return 4;
    }
}
```

## Interface Inheritance

- Sebelumnya kita sudah tahu kalo di Java, child class hanya bisa punya 1 class parent
- Namun berbeda dengan interface, sebuah child class bisa implement lebih dari 1 interface
- Bahkan interface pun bisa implement interface lain, bisa lebih dari 1. Namun jika interface ingin mewarisi interface lain, kita menggunakan kata kunci extends, bukan implements

Kode Interface Inheritance:

```java
public interface HasBrand {
    String getBrand();
}
```

```java
// Car.java

package belajar.java.oop;

public interface Car extends HasBrand {
    void drive();
}
```

Kode Multiple Interface Inheritance:

```java
public class Avanza implements Car, HasBrand {

    public String getBrand() {
        return "Toyota";
    }

    public boolean isMaintenance() {
        return false;
    }

    public void drive() {
        System.out.println("Drive Avanza");
    }
}
```

## Static Keyword

- Sebelumnya kita sudah sering melihat kata kunci static, namun belum pernah kita bahas
- Dengan menggunakan kata kunci static, kita bisa membuat field, method atau class bisa diakses langsung tanpa melalui object nya
- Perlu diingat, static hanya bisa mengakses static lainnya

**Static Dapat Digunakan di**

- `Field`, atau disebut class variable, artinya field tersebut bisa diakses langsung tanpa membuat object terlebih dahulu
- `Method`, atau disebut class method, artinya method tersebut bisa diakses langsung tanpa membuat object terlebih dahulu,
- `Block`, static block akan otomatis dieksekusi ketika sebuah class di load
- `Inner Class`, artinya inner class tersebut bisa diakses secara langsung tanpa harus membuat object outer class terlebih dahulu. Static pada inner class menyebabkan kita tidak bisa mengakses lagi object outer class nya

Kode Static Field:

```java
public class Constant {

    public static final String APPLICATION = "Belajar Java OOP";
    public static final Integer VERSION = 1;
}
```

Kode Static Method:

```java
public class MathUtil {

    public static int sum(int... values) {
        int total = 0;
        for (var value: values) {
            total += value;
        }
        return total;
    }
}
```

Kode Static Inner Class:

```java
public class Country {

    private String name;

    public static class City {

        private String name;

        public String getName() {
            return name;
        }
    }
}
```

Kode Static Block:

```java
public class Application {

    public static final int PROCESSOR;

    static {
        PROCESSOR = Runtime.getRuntime().availableProcessors();
    }
}
```

Kode Memanggil Static Members:

```java
System.out.println(Application.PROCESSOR);

System.out.println(Constant.APPLICATION);
System.out.println(Constant.VERSION);

System.out.println(MathUtil.sum(1,2,3,4,5));

Country.City city = new Country.City();
city.setName("Sorong");
```

Kode Static Import:

```java
import static belajar.java.statics.Contants.*;
import static belajar.java.statics.Application.PROCESSOR;
```

> [Source Material from Programmer Zaman Now](https://programmerzamannow.com)
