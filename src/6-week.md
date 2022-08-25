# Monday 
## Declare variable types in TypeScript
 ```typescript
    var kevin = 5
 ```
 ### Type inference in TypeScript
 
  ```typescript
    let x: number;
    let y =1;
    let z
    
    //Good
      x=1
    
    //Bad
      x="one"
      //because x is of type number 
      
   ///Type Any in TypeScript
     //works
      z=1
      z='one'
     //This works because z is of type any
 ```
 
 
### Any Type
 All types in TypeScript are subtypes of a single top type called the any type
 
 ### Primitive types in TypeScript
 #### Boolean type
 ```typescript
  let flag: boolean;
  let yes = true;
  let no = false;
 ```
 
 #### Number and BigInteger types
 ```typescript
let x: number;
let y = 0;
let z: number = 123.456;
let big: bigint = 100n; //This works as of Es2020
 ```
 
  #### String type
 ```typescript
let s: string;
let empty = "";
let abc = 'abc';
  
  //In TypeScript, you can also use template strings
  let firstName: string = "Mateo";
  let sentence: string = `My name is ${firstName}.
    I am new to TypeScript.`;
  console.log(sentence);
   
   /*
   output
   My name is Mateo.
    I am new to TypeScript.
*/
 ```
 
 #### The enum type
 Enumerations offer an easy way to work with sets of related constants. An enum, is a symbolic name for a set of values. Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.
 
 ```typescript
enum ContractStatus {
     Permanent,
     Temp,
     Apprentice
}
let employeeStatus: ContractStatus = ContractStatus.Temp;
console.log(employeeStatus);

///If you want the values to start with a different value, in this case 1, specify that in the enum declaration.

enum ContractStatus {
     Permanent = 5,
     Temp,
     Apprentice
}
```
<img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f5be82f2-4ba7-470f-8f3d-52847a4104a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220825%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220825T182606Z&X-Amz-Expires=86400&X-Amz-Signature=bec9401cbef99f4cdbf71da417e711502bb707c91d4a1951d2b3c74b7eaf42bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject' />



<img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3e106878-ed87-4ccf-897d-5c98a9d1cf70/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220825%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220825T182742Z&X-Amz-Expires=86400&X-Amz-Signature=691c6d21b068c7bc51095dae6199682dcf8654c2e64c5f1ee78edb9658e032df&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject' />

 
  #### The Any type
 ```typescript
let randomValue: any = 10;
randomValue = 'Mateo';   // OK
randomValue = true;      // OK

```
#### The Any type
 ```typescript
let randomValue: any = 10;
randomValue = 'Mateo';   // OK
randomValue = true;      // OK

//Remember that all the convenience of any comes at the cost of losing type safety. Type safety is one of the main motivations for using TypeScript. You should avoid using any when it's not necessary.
```

```
#### Unknown type
 ```typescript
let randomValue: unknown = 10;
randomValue = true;
randomValue = 'Mateo';

console.log(randomValue.name);  // Error: Object is of type unknown
randomValue();                  // Error: Object is of type unknown
randomValue.toUpperCase();      // Error: Object is of type unknown

```

#### Unknown type
|  Type      | predicate        |
| ---------- | ---------------- |
|string | typeof s === "string" |
|number | typeof n === "number" |
|boolean | typeof b === "boolean" |
|undefined | typeof undefined === "undefined"|
|function | typeof f === "function" |
|array | Array.isArray(a) |


###Union and intersection types in TypeScript 
####Union types 

```typescript
let multiType: number | boolean;
multiType = 20;         //* Valid
multiType = true;       //* Valid
multiType = "twenty";   //* Invalid
```
####Funtion Example
```typescript
function add(x: number | string, y: number | string) {
    if (typeof x === 'number' && typeof y === 'number') {
        return x + y;
    }
    if (typeof x === 'string' && typeof y === 'string') {
        return x.concat(y);
    }
    throw new Error('Parameters must be numbers or strings');
}
console.log(add('one', 'two'));  //* Returns "onetwo"
console.log(add(1, 2));          //* Returns 3
console.log(add('one', 2));      //* Returns error
```

####Intersection types
```typescritp
  interface Employee {
  employeeID: number;
  age: number;
}
interface Manager {
  stockPlan: boolean;
}
type ManagementEmployee = Employee & Manager;
let newManager: ManagementEmployee = {
    employeeID: 12345,
    age: 34,
    stockPlan: true
};
```

###Literal types
#####example

```typescript
   type testResult = "pass" | "fail" | "incomplete";
   let myResult: testResult;
   myResult = "incomplete";    //* Valid
   myResult = "pass";          //* Valid
   myResult = "failure";       //* Invalid
   
   In numbers
   
   type dice = 1 | 2 | 3 | 4 | 5 | 6;
   let diceRoll: dice;
   diceRoll = 1;    //* Valid
   diceRoll = 2;    //* Valid
   diceRoll = 7;    //* Invalid

```
###Collection types in TypeScript

####Arrays
```typescript
  let list: number[] = [1, 2, 3];
  
  //The second way uses a generic Array type, using the syntax Array<type>:
  let list: Array<number> = [1, 2, 3];
  
```

####Tuples

```typescript
   let person1: [string, number] = ['Marcia', 35];
   
   //This is bad because person1 no soport [string, number, boolean] just only soport [string, number]
   let person1: [string, number] = ['Marcia', 35, true];
```

####Exerise

  1
```typescript
  /*  EXERCISE 1
    TODO: Modify the code to add types to the variable declarations. 
    The resulting JavaScript should look the same as the original example when you're done. */

   let firstName: string;
   let lastName: string;
   let fullName: string;
   let age: number;
   let ukCitizen: boolean;

   firstName = 'Rebecca';
   lastName = 'Smith';
   age = 42;
   ukCitizen = false;
   fullName = firstName + " " + lastName;

   if (ukCitizen) {
       console.log("My name is " + fullName + ", I'm " + age + ", and I'm a citizen of the United Kingdom.");
   } else {
       console.log("My name is " + fullName + ", I'm " + age + ", and I'm not a citizen of the United Kingdom.");
   }
```
 2

```typescript
  /* EXERCISE 2
   TODO: Run the code as is and then modify it to have strongly typed variables. 
   Then, address any errors you find so that the result returned to a is 12. */

let x:number;
let y:number;
let a:number;

x = 5;
y = 7;
a = x + y;

console.log(a);

```

3

```typescript 
  /* EXERCISE 3
   TODO: In the following code, implement an enum type called Season that represents 
   the constants "Fall", "Winter", "Spring", and "Summer". Then, update the function so 
   you can pass in the season by referencing an item in the enum, for example 
   Season.Fall, instead of the literal string "Fall". */

function whichMonths(season) {
    let monthsInSeason: string;
    switch (season) {
        case "Fall":
            monthsInSeason = "September to November";
            break;
        case "Winter":
            monthsInSeason = "December to February";
            break;
        case "Spring":
            monthsInSeason = "March to May";
            break;
        case "Summer":
            monthsInSeason = "June to August";
    }
    return monthsInSeason;
}

console.log(whichMonths("Fall"));

```
