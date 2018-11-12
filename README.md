
# PHP OOP concepts.

## Classes and Objects 
	
Class is declared by using "class" keyword.

    class MyClass {
    
		// Public property.
		public $property1;
		
		// private property.
		private $property2;
		
		// protected property.
		protected $property3;
	
		// static property.
		static $static_property;
	
		// class constant.
		const CONST_VALUE = 5;
		
		// Initialised Property.
		const $property3 = "value";
		
		// Regular Function.
		public function functionName($arg) {
			// Logic..
		}
		
		// Static function.
		public static function staicFunctionName() {
			// Logic..
		}
    }
    
Class can be instantied by using **"new"** keyword.

     $object = new MyClass();

### Accessing class properties and methods.

Class properties and functions can be accessed by **"->"** operator.

    $object = new MyClass();
    // Accessing properties.
    $object->prop1;
    // Calling function.
    $object->functionName($arg);

Static properties, functions and classs constants can be accessed by **"::"** operator.

    // Access static property.
    MyClass::$static_property;
    
    // Access constant.
    MyClass::CONST_VALUE;
	
	// Static methods.
    MyClass::staicFunctionName();

## Functions
	
	/**
	 * Function declaration.
	 * 
    public function functionName($arg) {
		// Logic..
	}

A function can have as many arguments.

    public function functionName($arg1, $arg2, $arg3) {
	    // Logic..
    }
    
Arguments can be **type declared**.

    public function functionName(int $arg1, boolean $arg2, Class/Interface $arg3) {
    	// Logic..
    }

Function argument can have **default value**.

    public function functionName(int $arg1 = 1, bool $arg2 = TRUE) {
    	// Logic..
    }
Function **Return Type Declarations** 

    public function functionName() : int { 
	    // Valid
	    return 10;
	    // Invalid
	    return "string";
    }

### Acessing class properties from a class methods
	
Class properties and methods can be accessed from, another method by using **$this** keyword.
	
    public function myFunction() {
	    $this->property;
	    $this->otherFunction();
    }
Static properties and functions can be accessed using **self** keyword.

    public function myFunction() { 
	    self::$property; 
	    self::otherFunction(); 
    }

> Note: **$this** keyword cannot be used inside a static functions. It will throw an error.

## Inheritance

PHP supports multilevel inheritance and a class can extend another class using **extends** keyword.
Multiple inheritance in PHP is acheivable using **Interfaces**.

###  Extending classes

    class Parent {
	    public $prop1 = 10;
	    private $prop2 = 20;
	    protected $prop3 = 30;
		
		public function myFunction() {
			echo "Hi";
		}
    }
    class Child extends Parent {
		public $prop4 = 40;
		
		// Overloading
		public function myFunction() {
			echo "Hello";		
		}
    }
    
Public and protected properties and methods are inherited to child class. Private properties are only accessible only withing the class. 

To acess parent class properties, **parent** keyword is used.

    class Parent { 
	    public $prop = 10; 
	    public function myFunction() { 
		    echo "Hi"; 
		}
    }
    class Child extends Parent { 
	    public $prop = 20; 
	    public function myFunction() { 
		   echo parent::$prop; //20
		   echo parent::$prop: //10
		   echo parent::myFunction(); //Hi 
	    } 
    }
    
### Abstract classes

Abstract classes are the classes which cannot be instantiated, but can be extended. It should contain atleast one abstact method. An abstarct method is a method which has only declaration but no definition.

The subclass which extends an abstact class must define the implementation or else it should also be marked abstarct.

    abstarct class Vehicle {
	    // abstract method.
	    abstract protected function getWheels();
		
		// Common method.
		public function printWheels() {
			echo $this->getWheels();
		}
    }
    
	// Class marked as abstract since it is not defining the parent abstarct method implementation.
	abstract class Truck extends Vehicle {
	}
	
	class RegularTruck extends Truck {
		protected function getWheels() {
			return 6;
		}
	}
	class HeavyTruck extends Truck {
		protected function getWheels() {
			return 10;
		}
	}
	class Car extends Vehicle {
		protected function getWheels() {
			return 4;
		}
	}

### Interfaces
Interfaces are is same as abstact class except it can only contain abstract methods and the classes inherited form it must have to define all the methods.

> 1. Interfaces are declared using **interface** keyword.
> 2. All methods declred in an interface must be public.
> 3. One class can implement more than one interface.
> 4. One interface can extend another interface.

    interface Logger {
	    public function log($message);
    }
    
	class DBLogger implements Logger {
		public function log() {
			// Logic to log the message into db.
		}
	}
	
	class MailLogger implements Logger {
		public function log() {
			// Logic to log the message on email..
		}
	}
	
Apart from abstract methods, interfaces can contain constatnts also, but the constants cannto be overridden by the child classes. 

    interface Car { 
	    const WHEELS = 4; 
	    public function model();
    }
    class AudiD2 implements Car { 
	    public function model() {
		   echo "D2";
		}
    }
	echo Car::WHEELS; // 4
	echo AudiD2::WHEELS; // 4

### Traits

[Trait](http://php.net/manual/en/language.oop5.traits.php) is a concept of code reusability in PHP.  Since php is a single inheritance language, to allow developers to reuse sets of methods in several independent classes living in different class hierarchies, traits are used.

Traits are definded using the trait keyword and used in classes using use keyword. A class use multiple keywords.

    interface SmartPhone {
		public function model();
		public function osName();
		public function developer();
	}
	
	trait Android {
		public function osName(){
			echo "Android";
		}
		public function developer(){
			echo "Googe";
		}
	}
	
	trait Ios {
		public function osName(){
			echo "IOS";
		}
		public function developer(){
			echo "Apple";
		}
	}
	
	class MotoG im[l{}
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzM0MzI2NjEsODEwMTQyMTc2LC0xMz
AyMDYwODMsLTE2Njc0NDE4NjUsLTI2NzQxOTEzMiw5ODQyNDE2
NDAsMTA4NzA0NDM5LC01NjU3MDExNSwtMTE0NjgyNTMyNywzNz
Y4NDM4MSwxMzc5MTk0Njk4LDM1MDUyNjAzNSwxMTY0MjY4NTc5
LDE1ODM2MDE4NDYsLTEyOTUzODk1NjcsLTI1MjgyMTk3OSwtND
A4NjMxODYyLDEwODAwNzM1MDEsLTY2NTE2ODc3NSwxNzU3Mjg0
MTk1XX0=
-->