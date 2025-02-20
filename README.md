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




