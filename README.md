# TypeScript-Notes
## TypeScript Introduction 
TypeScript is typed JavaScript. TypeScript adds types to JavaScript to help you speed up the development by catching errors before you even run the JavaScript code.  
TypeScript is an open-source programming language that builds on top of JavaScript. It works on any web browser, any OS, and any environment that JavaScript runs.  
1. TypeScript is a superset of JavaScript.  
2. TypeScript builds on top of JavaScript. First, you write the TypeScript code. Then, you compile the TypeScript code into plain JavaScript code using a TypeScript compiler.  
3. Once you have the plain JavaScript code, you can deploy it to any environment that JavaScript runs.  
4. TypeScript files use the .ts extension rather than the .js extension of JavaScript files.  

![image](https://github.com/user-attachments/assets/1fd8641a-d8fc-4393-b304-c6f2c7632402)  

5. TypeScript uses the JavaScript syntaxes and adds additional syntaxes for supporting Types.
6. If you have a JavaScript program without any syntax errors, it is a TypeScript program. This means that all JavaScript programs are TypeScript programs. This is very helpful if you migrate an existing JavaScript codebase to TypeScript.
   
![image](https://github.com/user-attachments/assets/6d6fac26-07cf-4acc-91b4-35713196cd98)  


## Why TypeScript
The main goals of TypeScript are:
1. Introduce optional types to JavaScript.
2. Implement planned features of future JavaScript, a.k.a. ECMAScript Next or ES Next to the current JavaScript.

### TypeScript improves your productivity while helping avoid bugs
Types increase productivity by helping you avoid many mistakes. By using types, you can catch bugs at the compile time instead of having them occur at runtime.<br /><br />
For example, the following function adds two numbers x and y:<br />
`
function add(x, y) {
   return x + y;
}
`<br /><br />
If you get the values from HTML input elements and pass them into the function, you may get an unexpected result:<br />
`let result = add(input1.value, input2.value);
console.log(result); // result of concatenating strings`  

For example, if users entered **10** and **20**, the **add()** function would return **1020**, instead of **30**.  

The reason is that **input1.value** and **input2.value** are **strings**, not **numbers**. When you use the operator **+** to add two strings, it concatenates them into a single string.  

When you use TypeScript to specify the type for the parameters like this explicitly:  
`
function add(x: number, y: number) {
   return x + y;
}
`  

In this function, we added the number types to the parameters. The function **add()** will accept only numbers, not any other values.

When you invoke the function as follows:<br />
`
let result = add(input1.value, input2.value);
`<br /><br />
The TypeScript compiler will issue an error if you compile the **TypeScript** code into **JavaScript**. Hence, you can prevent the error from happening at runtime.  

### TypeScript brings the future JavaScript to today
TypeScript supports the upcoming features planned in the ES Next for the current JavaScript engines. It means you can use the new JavaScript features before web browsers (or other environments) fully support them. <br />

### Summary
1. TypeScript is a superset of JavaScript.
2. TypeScript adds type to the JavaScript and helps you avoid potential bugs that occur at runtime.
3. TypeScript also implements the future features of JavaScript.

## Setup
1. Install Node.js
2. Install typescript: `npm install -g typescript` <br/>
Check typescript compiler version: `tsc --v` <br/>
3. If you want to run TypeScript code directly on Node.js without precompiling, you can use the tsx module: `npm install -g tsx` <br/>

### Summary
1. A TypeScript compiler compiles the TypeScript into JavaScript.
2. Use the tsc command to compile a TypeScript file to a JavaScript file.
3. Use the tsx module to run TypeScript directly on Node.js without precompiling it to JavaScript.

## TypeScript “Hello, World!”
1. Create a new directory to store the code, e.g., helloworld.
2. Create a new TypeScript file called app.ts. The extension of a TypeScript file is .ts
3. Type the following source code in the app.ts file:<br/>
`let message: string = 'Hello, World!';
console.log(message);`
4. Type the following command on the Terminal to compile the app.ts file:<br/>
`tsc app.ts`
5. If everything is fine, you’ll see a new file called `app.js` is generated by the TypeScript compiler.
6. To run the app.js file in Node.js, you use the following command:<br/>
`node app.js`
7. If you installed the tsx module, you can use just one command to run the TypeScript file directly on Node.js without precompiling it to JavaScript:<br/>
`tsx app.ts`

## TypeScript Benefits
1. TypeScript adds a type system to help you avoid many problems with dynamic types in JavaScript.
2. TypeScript implements the future features of JavaScript a.k.a ES Next so you can use them today.

## Dynamic Types in JavaScript
JavaScript is dynamically typed. Unlike statically typed languages such as Java or C#, values have types instead of variables.<br/><br/>
`let box;
box = "hello";
box = 100;`
<br/>
<br/>
The type of the box variable changes based on the value assigned to it.<br/>
To find the type of the box variable at runtime, you use the **typeof operator**<br/>
```
let box;
console.log(typeof(box)); // undefined

box = "Hello";
console.log(typeof(box)); // string

box = 100;
console.log(typeof(box)); // number
```
<br/>
The first statement defines a variable box without assigning a value in this example. Its type is undefined.<br/>
Then, we assign the literal string "Hello" to box variable and show its type. The type of the box variable changes to string.<br/>
Finally, we assign 100 to the box variable. This time, the type of the box variable changes to number.<br/>
As you can see, as soon as the value is assigned, the type of the variable changes.<br/>
And you don’t need to explicitly tell JavaScript the type. JavaScript will automatically infer the type from the value.<br/>
Dynamic types offer flexibility. However, they also lead to problems.<br/>

### Problems with dynamic types
Suppose you have a function that returns a product object based on an id:<br/>
```
function getProduct(id){
  return {
    id: id,
    name: `Awesome Gadget ${id}`,
    price: 99.5
  }
}
```
<br/>
The following uses the getProduct() function to retrieve the product with id 1 and show its data: <br/> 

```
const product = getProduct(1);
console.log(`The product ${product.Name} costs $${product.price}`);
```

<br/>
Output:<br/>
The product undefined costs $99.5 <br/>

It isn’t what we expected.<br/>

The issue with this code is that the product object doesn’t have the Name property. It has the name property with the first letter n in lowercase.
<br/>
However, you can only know it until you run the script. <br/>
Referencing a property that doesn’t exist on the object is a common issue when working in JavaScript. <br/>
The following example defines a new function that outputs the product information to the console: <br/>
```
const showProduct = (name, price)  => {
  console.log(`The product ${name} costs $${price}.`);
};
```
<br/>
The following uses the getProduct() and showProduct() functions: <br/>

```
const product = getProduct(1);
showProduct(product.price, product.name);
```

<br/>
The product 99.5 costs $Awesome Gadget 1 <br/>
This time we pass the arguments in the wrong order to the showProduct() function. This is another common problem that you often have when working with JavaScript.<br/>
This is why TypeScript comes into play.<br/>

### How Typescript solves problems of dynamic types
To fix the problem of referencing a property that doesn’t exist on an object, you do the following steps:<br/>

First, define the “shape” of the product object using an interface.<br/>
```
interface Product{
    id: number,
    name: string,
    price: number
};
```
<br/>

Second, explicitly use the Product type as the return type of the getProduct() function:<br/>
```
function getProduct(id) : Product{
  return {
    id: id,
    name: `Awesome Gadget ${id}`,
    price: 99.5
  }
}
```
<br/>
When you reference a property that doesn’t exist, the code editor will inform you immediately: <br/>

```
const product = getProduct(1);
console.log(`The product ${product.Name} costs $${product.price}`);
```

<br/>
The code editor highlighted the following error on the Name property<br/><br/>
![image](https://github.com/user-attachments/assets/8f6fde4d-af51-401c-b62c-ddca6869d4da)

<br/><br/>
And when you hover the mouse cursor over the error, you’ll see a hint that helps you to solve the issue:<br/><br/>
![image](https://github.com/user-attachments/assets/e5f1e923-b471-408a-9968-c692d3d0b02d)

<br/><br/>
To solve the problem of passing the arguments in the wrong order, you explicitly assign types to function parameters: <br/>

```
const showProduct = (name: string, price:number)  => {
  console.log(`The product ${name} costs $${price}.`);
};
```

<br/>
And when you pass the arguments of the wrong types to the showProduct() function, you’ll receive an error: <br/><br/>

```
const product = getProduct(1);
showProduct(product.price, product.name);
```

<br/>

### Summary
1. JavaScript is dynamically typed, providing flexibility but also leading to many problems.
2. TypeScript adds an optional type system to JavaScript to solve these problems.

## TypeScript Types
### What is a type in TypeScript

In TypeScript, a type is a convenient way to refer to different properties and functions that a value has. <br/>
A value is anything you can assign to a variable e.g., a number, a string, an array, an object, and a function <br/>
For example, see the following value: `'Hello'` <br/>
When you look at this value, you can say it is a string. This value has properties and methods that a string has. <br/>

For example, the 'Hello' value has a property called length that returns the number of characters: <br/>
`console.log('Hello'.length); // 5`

It also has many methods like match(), indexOf(), and toLocaleUpperCase(). For example: <br/>
`console.log('Hello'.toLocaleUpperCase()); // HELLO` <br />

When you look at the value 'Hello' and describe it by listing the properties and methods, it would be inconvenient. <br />

A shorter way to refer to a value is to assign it a type. In this example, you say 'Hello' is a string. Then, you know that you can use the properties and methods of a string for the value 'Hello' <br />

In conclusion, in TypeScript:

1. a type is a label that describes the different properties and methods that a value has
2. every value has a type.

### Types in TypeScript
TypeScript inherits the built-in types from JavaScript. TypeScript types are categorized into:

1. Primitive types.
2. Object types.

### Primitive types
![image](https://github.com/user-attachments/assets/dae2fcbb-2560-4fae-aa56-32dc6a3b284e)  

### Object Types
Object types are functions, arrays, classes, etc.

### Purposes of types in TypeScript
There are two main purposes of types in TypeScript:

1. First, types are used by the TypeScript compiler to analyze your code for errors.
2. Second, types allow you to understand what values are associated with variables.

### Summary
1. In TypeScript, every value is associated with a type.
2. A type is a label that describes the properties and methods that a value has.
3. TypeScript compiler uses types to analyze your code for hunting bugs and errors.

## Understanding Type Annotations in TypeScript
TypeScript uses type annotations to specify explicit types for identifiers such as variables, functions, objects, etc. <br/>

TypeScript uses the syntax : type after an identifier as the type annotation, which type can be any valid type. <br/>

Once an identifier is annotated with a type, it can be used as that type only. If the identifier is used as a different type, the TypeScript compiler will issue an error. <br/>

### Type annotations in variables and constants
The following syntax shows how to specify type annotations for variables and constants: <br/>
```
let variableName: type;
let variableName: type = value;
const constantName: type = value;
```
<br/> 
In this syntax, the type annotation comes after the variable or constant name and is preceded by a colon (:). <br/> 

The following example uses number annotation for a variable: <br/> 
`
let counter: number;
`
<br/> 
After this, you can only assign a number to the counter variable: <br/> 
`
counter = 1;
`
<br/> 
If you assign a string to the counter variable, you’ll get an error: <br/> 

```
let counter: number;
counter = 'Hello'; // compile error
```

<br/> 
Error: <br/> 

`
Type '"Hello"' is not assignable to type 'number'.
`

<br/> 
You can both use a type annotation for a variable and initialize it in a single statement like this: <br/> 

`let counter: number = 1;`

<br/> 
The following shows other examples of primitive type annotations: <br/> 

```
let name: string = 'John';
let age: number = 25;
let active: boolean = true;
```

<br/> 

## Type annotation examples
### Arrays

To annotate an array type you use a specific type followed by a square bracket : type[] : <br/>

```
let arrayName: type[];
```

 <br/>
For example, the following declares an array of strings: <br/>

```
let names: string[] = ['John', 'Jane', 'Peter', 'David', 'Mary'];
```

 <br/>

 ### Objects
To specify a type for an object, you use the object type annotation. For example: <br/>

```
let person: {
  name: string;
  age: number;
};

person = {
  name: 'John',
  age: 25,
}; // valid

```

<br/>

In this example, the person object only accepts an object with two properties: name with the string type and age with the number type.

### Function arguments & return types
The following shows a function annotation with parameter type annotation and return type annotation: <br />
```
let greeting : (name: string) => string;
```

<br/>

In this example, you can assign any function that accepts a string and returns a string to the greeting variable: <br />

```
greeting = function (name: string) {
    return `Hi ${name}`;
};
```

<br />


The following causes an error because the function that is assigned to the greeting variable doesn’t match its function type. <br />

```
greeting = function () {
    console.log('Hello');
};
```

Error: <br />
```
Type '() => void' is not assignable to type '(name: string) => string'. Type 'void' is not assignable to type 'string'.
```

### Summary
Use type annotations with the syntax : [type] to explicitly specify a type for a variable, function, function return value, etc.

## TypeScript Type Inference
Type inference describes where and how TypeScript infers types when you don’t explicitly annotate them. <br/>

### Basic type inference
When you declare a variable, you can use a type annotation to explicitly specify a type for it. For example: <br />

```
let counter: number;
```

<br/>
However, if you initialize the counter variable with a number, TypeScript will infer the type of the counter to be number. For example: <br/>

```
let counter = 0;
```

<br/>
It is equivalent to the following statement: <br/>

```
let counter: number = 0;
```

<br />
Likewise, when you assign a function parameter a value, TypeScript infers the type of the parameter to the type of the default value. For example: <br/>

```
function setCounter(max=100) {
    // ...
}
```

In this example, TypeScript infers the type of the max parameter to be number. <br />

```
function setCounter(max=100) {
    // ...
}
```

<br />

Similarly, TypeScript infers the following return type of the increment() function as number: <br />

```
function increment(counter: number) {
    return counter++;
}
```

<br/>
It is the same as: <br/>

```
function increment(counter: number) : number {
    return counter++;
}
```

<br/>

### The best common type algorithm

Consider the following assignment: <br />

```
let items = [1, 2, 3, null];
````

<br />
To infer the type of items variable, TypeScript needs to consider the type of each element in the array.
<br />
It uses the best common type algorithm to analyze each candidate type and select the type that is compatible with all other candidates.
<br />
In this case, TypeScript selects the number or null array type (number | null) []) as the best common type. Note that the | means the OR operator in types.
<br />
If you add a string to the items array, TypeScript will infer the type for the items as an array of numbers and strings: (number | string)[]
<br />

```
let items = [1, 2, 3, 'Cheese'];
```

<br />

### Contextual typing
TypeScript uses the locations of variables to infer their types. This mechanism is known as contextual typing. For example: <br />

```
document.addEventListener('click', function (event) {
    console.log(event.button); 
});
```

<br />
In this example, TypeScript knows that the event parameter is an instance of MouseEvent because of the click event.
<br />
However, when you change the click event to the scroll the event, TypeScript will issue an error:
<br />

```
document.addEventListener('scroll', function (event) {
    console.log(event.button); // compile error
});
```

<br />

Error:
<br />

```
Property 'button' does not exist on type 'Event'.(2339)
```

<br />

TypeScript knows that the event in this case, is an instance of UIEvent, not a MouseEvent. And UIEvent does not have the button property, therefore, TypeScript throws an error.
<br />
You will find contextual typing in many cases such as arguments to function calls, type assertions, members of objects and array literals, return statements, and right-hand sides of assignments.
<br />

### Type inference vs. Type annotations
The following shows the difference between type inference and type annotations: <br />

Type inference	- TypeScript guesses the type	 <br />

Type annotations - You explicitly tell TypeScript the type <br />

### When do you use type inference and type annotations?
<br />
In practice, you should always use the type inference as much as possible. You use the type annotation in the following cases:
<br />
1. When you declare a variable and assign it a value later.
2. When you want a variable that can’t be inferred.
3. When a function returns the any type, you need to clarify the value.

### Summary
1. Type inference occurs when you initialize variables, set parameter default values, and determine function return types.
2. TypeScript uses the best common type algorithm to select the best candidate types that are compatible with all variables.
3. TypeScript also uses contextual typing to infer types of variables based on the locations of the variables.

## TypeScript Number
All numbers in TypeScript are either **floating-point values or big integers**. The floating-point numbers have the type **number** while the big integers get the type **bigint**.
<br/>
### The number type
The following shows how to declare a variable that holds a floating-point value: <br/>
`let price: number;`
<br />
Alternatively, you can initialize the price variable to a number: <br />
`let price = 9.95;`
<br />

### Big Integers
The big integers represent the whole numbers larger than 2 power 53 – 1. A Big integer literal has the **n** character at the end of an integer literal like this: <br />
`let big: bigint = 9007199254740991n;`
<br/>

```
JavaScript has the Number type (with the letter N in uppercase) that refers to the non-primitive boxed object. You should not use this Number type as much as possible in TypeScript.
```

<br/>

### Summary
All numbers in TypeScript are either **floating-point values** that get the **number type** or **big integers** that get the **bigint type**.
Avoid using the Number type as much as possible.

## TypeScript String
Like JavaScript, TypeScript uses double quotes (") or single quotes (') to surround string literals: <br/>

```
let firstName: string = 'John';
let title: string = "Web Developer";
```

<br/>
TypeScript also supports template strings that use the backtick (`) to surround characters. <br/>

```
let firstName: string = `John`;
let title: string = `Web Developer`;
let profile: string = `I'm ${firstName}. 
I'm a ${title}`;

console.log(profile);
```

<br/>

Output <br/>

```
I'm John. 
I'm a Web Developer.
```

<br />

### Summary
1. In TypeScript, all strings get the string type. 
2. Like JavaScript, TypeScript uses double quotes ("), single quotes ('), and backtick (`) to surround string literals.


## TypeScript Boolean
The TypeScript boolean type has two values: true and false. The boolean type is one of the primitive types in TypeScript. <br/>

```
let pending: boolean;
pending = true;
// after a while
// ..
pending = false;
```

<br/>

### Boolean operator
To manipulate boolean values, you use the boolean operators. TypeScript supports common boolean operators: <br/>

```
&&	   Logical AND operator
||	   Logical OR operator
!	   Logical NOT operator
```

<br/>

```
// NOT operator
const pending: boolean = true;
const notPending = !pending; // false
console.log(result); // false

const hasError: boolean = false;
const completed: boolean = true;

// AND operator
let result = completed && hasError; 
console.log(result); // false

// OR operator
result = completed || hasError; 
console.log(result); // true
```

<br/>

### Type annotations for boolean

```
let completed = true;
```

<br/>
Is same as:
<br/>

```
let completed: boolean = true;
```

<br/>
JavaScript has the Boolean type that refers to the non-primitive boxed object. The Boolean type has the letter B in uppercase, which is different from the boolean type. <br/>

It’s a good practice to avoid using the Boolean type. <br/>

### Summary
1. TypeScript boolean type has two values true and false.
2. Use the boolean keyword to declare boolean variables.
3. Do not use Boolean type unless you have a good reason to do so.

## TypeScript object Type

The TypeScript object type represents all values that are not in primitive types. <br/>

The following are primitive types in TypeScript: <br/>
 
1. number
2. bigint
3. string
4. boolean
5. null
6. undefined
7. symbol

<br/>

```
let employee: object;

employee = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};

console.log(employee);
```

<br/>
If you reassign a primitive value to the employee object, you’ll get an error : <br/>

```
employee = "Jane";
```

<br/>

```
Error:
error TS2322: Type '"Jane"' is not assignable to type 'object'.
```

<br/>
To explicitly specify properties of the employee object, you first use the following syntax to declare the employee object:
<br/>

```
let employee: {
    firstName: string;
    lastName: string;
    age: number;
    jobTitle: string;
};
```

<br/>
And then assign the employee object to a literal object with the described properties:
<br/>

```
employee = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};
```

<br/>

Or you can combine both syntaxes in the same statement like this:
<br/>

```
let employee: {
    firstName: string;
    lastName: string;
    age: number;
    jobTitle: string;
} = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};
```

<br/>

### object vs. Object
TypeScript has another type called Object with the letter O in uppercase. It’s important to understand the differences between them. <br/>
 
The object type represents all non-primitive values while the Object type describes the functionality of all objects. <br/>

For example, the Object type has the toString() and valueOf() methods that can be accessible by any object. <br/>

### Summary
1. The TypeScript object type represents any value that is not a primitive value.
2. The Object type, however, describes functionality that is available on all objects.
3. The empty type {} refers to an object that has no property on its own.



