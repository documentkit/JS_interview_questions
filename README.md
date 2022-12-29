# JavaScript BASICS...

### ```1. What are the different data types present in javascript?```
To know the type of a JavaScript variable, we can use the typeof operator.

#### Primitive types:

* String - It represents a series of characters and is written with quotes. A string can be represented using a single or a double quote.
##### Example:

```JavaScript
var str = "Vivek Singh Bisht"; //using double quotes
var str2 = 'John Doe'; //using single quotes
```

* Number - It represents a number and can be written with or without decimals.
##### Example:

```JavaScript
var x = 3; //without decimal
var y = 3.6; //with decimal
```

* BigInt - This data type is used to store numbers which are above the limitation of the Number data type. It can store large integers and is represented by adding “n” to an integer literal.
##### Example:

```JavaScript
var bigInteger =  234567890123456789012345678901234567890;
```

* Boolean - It represents a logical entity and can have only two values : true or false. Booleans are generally used for conditional testing.
##### Example:

```JavaScript
var a = 2;
var b =  3;
var c =  2;
(a == b) // returns false
(a == c) //returns true
```

* Undefined - When a variable is declared but not assigned, it has the value of undefined and it’s type is also undefined.
##### Example:

```JavaScript
var x; // value of x is undefined
var y = undefined; // we can also set the value of a variable as undefined
```

* Null - It represents a non-existent or a invalid value.
##### Example:

```JavaScript
var z = null;
```

* Symbol - It is a new data type introduced in the ES6 version of javascript. It is used to store an anonymous and unique value.
##### Example:

```JavaScript
var symbol1 = Symbol('symbol');
typeof of primitive types :
typeof "John Doe" // Returns "string"
typeof 3.14 // Returns "number"
typeof true // Returns "boolean"
typeof 234567890123456789012345678901234567890n // Returns bigint
typeof undefined // Returns "undefined"
typeof null // Returns "object" (kind of a bug in JavaScript)
typeof Symbol('symbol') // Returns Symbol
```

#### Non-primitive types:

* Primitive data types can store only a single value. To store multiple and complex values, non-primitive data types are used.
* Object - Used to store collection of data.
##### Example:

```JavaScript
// Collection of data in key-value pairs

var obj1 = {
   x:  43,
   y:  "Hello world!",
   z: function(){
      return this.x;
   }
}
      
// Collection of data as an ordered list
     
var array1 = [5, "Hello", true, 4.1];
```

``` Note- It is important to remember that any data type that is not a primitive data type, is of Object type in javascript.```

### ```2. Explain Hoisting in javascript.```

#### Hoisting is the default behaviour of javascript where all the variable and function declarations are moved on top. This means that irrespective of where the variables and functions are declared, they are moved on top of the scope. The scope can be both local and global.

##### Example 1:

```JavaScript
hoistedVariable = 3;
console.log(hoistedVariable); // outputs 3 even when the variable is declared after it is initialized	
var hoistedVariable;
```

##### Example 2:

```JavaScript
hoistedFunction();  // Outputs " Hello world! " even when the function is declared after calling

function hoistedFunction(){ 
  console.log(" Hello world! ");
} 
```

##### Example 3:

```JavaScript
// Hoisting takes place in the local scope as well
function doSomething(){
  x = 33;
  console.log(x);
  var x;
} 
// doSomething(); Outputs 33 since the local variable “x” is hoisted inside the local scope
```

``` Note - Variable initializations are not hoisted, only variable declarations are hoisted:```
```JavaScript
var x;
console.log(x); // Outputs "undefined" since the initialization of "x" is not hoisted
x = 23;
```
``` Note - To avoid hoisting, you can run javascript in strict mode by using “use strict” on top of the code:```
```JavaScript
"use strict";
x = 23; // Gives an error since 'x' is not declared
var x;
```

### ```3. Why do we use the word “debugger” in javascript?```

#### The debugger for the browser must be activated in order to debug the code. Built-in debuggers may be switched on and off, requiring the user to report faults. The remaining section of the code should stop execution before moving on to the next line while debugging.

### ```4. Difference between “ == “ and “ === “ operators.```

#### Both are comparison operators. The difference between both the operators is that “==” is used to compare values whereas, “ === “ is used to compare both values and types.

##### Example:

```JavaScript
var x = 2;
var y = "2";
(x == y)  // Returns true since the value of both x and y is the same
(x === y) // Returns false since the typeof x is "number" and typeof y is "string"
```

### ```5. Difference between var and let keyword in javascript.```

#### Some differences are:
#### 1: From the very beginning, the 'var' keyword was used in JavaScript programming whereas the keyword 'let' was just added in 2015.
#### 2: The keyword 'Var' has a function scope. Anywhere in the function, the variable specified using var is accessible but in ‘let’ the scope of a variable declared with the 'let' keyword is limited to the block in which it is declared. Let's start with a Block Scope.
#### 3: In ECMAScript 2015, let and const are hoisted but not initialized. Referencing the variable in the block before the variable declaration results in a ReferenceError because the variable is in a "temporal dead zone" from the start of the block until the declaration is processed.

### ```6. Explain Implicit Type Coercion in javascript.```

#### Implicit type coercion in javascript is the automatic conversion of value from one data type to another. It takes place when the operands of an expression are of different data types.

* String coercion - String coercion takes place while using the ‘ + ‘ operator. When a number is added to a string, the number type is always converted to the string type.

##### Example 1:

```JavaScript
var x = 3;
var y = "3";
x + y // Returns "33" 
```

##### Example 2:

```JavaScript
var x = 24;
var y = "Hello";
x + y   // Returns "24Hello"; 
```
```Note - ‘ + ‘ operator when used to add two numbers, outputs a number. The same ‘ + ‘ operator when used to add two strings, outputs the concatenated string:```
```JavaScript
var name = "Abhinav";
var surname = " Anand";
name + surname //Returns "Abhinav Anand"
```

Let’s understand both the examples where we have added a number to a string,

When JavaScript sees that the operands of the expression x + y are of different types ( one being a number type and the other being a string type ), it converts the number type to the string type and then performs the operation. Since after conversion, both the variables are of string type, the ‘ + ‘ operator outputs the concatenated string “33” in the first example and “24Hello” in the second example.

```Note - Type coercion also takes place when using the ‘ - ‘ operator, but the difference while using ‘ - ‘ operator is that, a string is converted to a number and then subtraction takes place.```
```JavaScript
var x = 3;
Var y = "3";
x - y    //Returns 0 since the variable y (string type) is converted to a number type
```

* Boolean Coercion - Boolean coercion takes place when using logical operators, ternary operators, if statements, and loop checks. To understand boolean coercion in if statements and operators, we need to understand truthy and falsy values.

Truthy values are those which will be converted (coerced) to true. Falsy values are those which will be converted to false.

All values except false, 0, 0n, -0, “”, null, undefined, and NaN are truthy values.

#### If statements:

##### Example:

```JavaScript
var x = 0;
var y = 23;
        
if(x) { console.log(x) }   // The code inside this block will not run since the value of x is 0 (Falsy)  
        
if(y) { console.log(y) }    // The code inside this block will run since the value of y is 23 (Truthy)
```

#### Logical operators: Logical operators in javascript, unlike operators in other programming languages, do not return true or false. They always return one of the operands.

```OR``` ( | | ) operator - If the first value is truthy, then the first value is returned. Otherwise, always the second value gets returned.

```AND``` ( && ) operator - If both the values are truthy, always the second value is returned. If the first value is falsy then the first value is returned or if the second value is falsy then the second value is returned.

##### Example:
```JavaScript
var x = 220;
var y = "Hello";
var z = undefined;
        
x | | y    // Returns 220 since the first value is truthy
        
x | | z   // Returns 220 since the first value is truthy
        
x && y    // Returns "Hello" since both the values are truthy
        
y && z   // Returns undefined since the second value is falsy
        
if( x && y ){ 
  console.log("Code runs" ); // This block runs because x && y returns "Hello" (Truthy)
}   
        
if( x || z ){
  console.log("Code runs");  // This block runs because x || y returns 220(Truthy)
}
```

* Equality Coercion - Equality coercion takes place when using ‘ == ‘ operator. As we have stated before

``` The ‘ == ‘ operator compares values and not types. ```

While the above statement is a simple way to explain == operator, it’s not completely true

The reality is that while using the ‘==’ operator, coercion takes place.

The ‘==’ operator, converts both the operands to the same type and then compares them.

##### Example:
```JavaScript
var a = 12;
var b = "12";
a == b // Returns true because both 'a' and 'b' are converted to the same type and then compared. Hence the operands are equal.
```
Coercion does not take place when using the ‘===’ operator. Both operands are not converted to the same type in the case of ‘===’ operator.

##### Example:
```JavaScript
var a = 226;
var b = "226";

a === b // Returns false because coercion does not take place and the  operands are of different types. Hence they are not equal. 
``` 
