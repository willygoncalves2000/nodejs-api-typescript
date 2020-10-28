# :arrow_forward: Node.js API with TypeScript
This is a simple Node.js API developed with TypeScript.

## :rocket: Tecnologies
* Node.js
* Express.js
* TypeScript

## :ballot_box_with_check: Using
> Clone this repository:
```
$ git clone https://github.com/willygoncalves2000/nodejs-api-typescript
```
> Go into the repository:
```
$ cd api-nodejs-typescript
```
> Install compiler:
```
$ sudo npm install -g typescript
```
> Install dependencies:
```
$ npm install
```
> Run compiler:
```
$ tsc
```
> Run app:
```
$ npm start
```

## :information_source: What is TypeScript
TypeScript (TS) is a superset of JavaScript (JS), that is, it extends the language
JavaScript. Unlike JS, TS cannot be interpreted by the browser, so we need a compiler.
TS offers us a better development experience because adds resources that are only 
available in the development process and that help to write better and cleaner 
code, and avoid unwanted errors.

But how does TS really help us?

Let's imagine that we have a function that takes two numbers as parameters and that
return their sum:
```
function add(num1, num2) {
  return num1+num2;
}
console.log(add('2', '3'));
//------- console ------ 
// 23
//---------------------- 
```
Note that when calling the *add* function, we are passing two values that are not
numbers in fact, since they are in quotes. So JS doesn't recognize them as numbers,
but as a *string* and, when using the + operator, we are concatenating (joining)
these two *strings*. However, this was not really our goal, because we wanted
add two numbers, so the function should return *5*.

And that's where TypeScript comes in. With it we can define the typing of the value that
we are receiving as a parameter:
```
function add(num1: Number, num2: Number) {
  return num1+num2;
}
console.log(add('2', '3')); //Isso vai apontar erro
console.log(add(2, 3)); 
//------- console ------ 
// 5
//---------------------- 
```
Realize that we are now defining that the values we are receiving in the
function parameters are of type *Number*. So when we call *add* passing
values between '' will be accused *erro*, because this is not the type we are expecting
in function. So we are forced to actually pass a number, and the function goes
work as expected.

Note that, without defining the typing (which was possible thanks to TypeScript), the
function did not act as we wanted and, although in this case we knew the reason and
we could fix it, at no time was a *error* accused what was the problem.

## :gear: TypeScript Setup
* Create a file with extension *.ts* (ex.: app.ts);

* Install the compiler
    ```
    sudo npm install -g typescript
    ```
* Run the command:
    ```
    tsc app.ts
    ```
    This will create an * app.js * file, as this compiler will convert the TypeScript to JavaScript.

* It is possible to create a TypeScript configuration file using the command: 
    ```
    tsc --init
    ```
    This will create the *tsconfig.json* file that will hold the TypeScript settings.

* Run the command *npm install* to create a project controlled by *npm*, where we can
install dependencies.

* Install *express*:
    ```
    npm install express
    ```

* Install *body-parser*:
    ```
    npm install body-parser
    ```
PS.: It may be necessary to install the typing of these packages. It is recommended that this
installed as a development dependency:
    ```
    npm install -D @types/express
    ```

## :wrench: tsconfig.json Setup
Not many changes are needed in this TypeScript configuration file,
however we will do some to improve our folder structure. 
As we have already seen, the browser does not understand TypeScript, so we use the compiler
to convert our code to JavaScript. When we run the command *tsc* all
the files with extension *.ts* will be converted to *.js*, and both files
will be saved in the same location.
```
---app.js
---app.ts
---package.json
---tsconfig.json

```
As the application grows, our folder structure will become confused and,
furthermore, we will not be changing the *.js* files directly, so it would be interesting
leave them in an exclusive folder. For this, we will create a folder called *dist* that
will store the *.js* files and a *src* folder that will store the *.ts* files
in which we are encoding:
```
----dist
------app.js
----src
------app.ts
----package.json
----tsconfig.json
```
To make this work, we need to change two settings in the file *tsconfig.json*:
```
    "outDir": "./dist",                 
    "rootDir": "./src",  
```
With the first option we are defining where the files will go after being compiled.
In the second, we are specifying where the TypeScript files are, where we will
in fact write our code.
To test this new configuration and folder structure, just run the command
*tsc* to compile the files *.ts*. If the compiled files (*.js*) are
saved in the / dist folder, then everything is working as we would like.

## :mag_right: Type Aliases & Interfaces
**Type Aliases** and **Interfaces** allow you to define the structure of an object and name
types. To define a **Type Aliases** we can use the word **type**, while
that to define a **Interface** we use the word **interface**:
```
type Todo = { id: string; text: string };

interface Todo {
  id: string;
  text: string;
}
```
In the code above we are creating an *Todo* object that can be used as
type.
If we are defining an object (as in the code above), we can use
both **Aliases** and **Interfaces** (although **Interface** is more common, it is not
required).
The big difference is that **Interfaces** can be used to force classes to
implement certain method and features.

## :pushpin: Generics
*Generic* in TypeScript is a type that interacts with another type, for example,
an array. The array is a type by itself, but it integrates with another type, the type
data inside the array.

Let's create an array called *todos*:
```
let todos = [];
```
Until that moment, this array could receive values of any type (string,
int, float, object, etc...). However, with TypeScript we can define typing
of this array. We could simply say that it is a array of *strings*:
```
let todos: string[] = [];
```
But, instead, we want this to be an array of objects, which has
**defined fields** with **defined typing**. For this we created the **interface** *Todo*,
and we say that this array is of the *Todo* type:
```
interface Todo {
  id: string;
  text: string;
}

let todos: Todo[] = [];
```
Therefore, in the code above we have an *Todo* interface that will define the internal type of the array
*todos*. Therefore, inside the array we will have two fields: id (string) and
text (string).

