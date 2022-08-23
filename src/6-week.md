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
<img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f5be82f2-4ba7-470f-8f3d-52847a4104a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220823%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220823T001615Z&X-Amz-Expires=86400&X-Amz-Signature=2460789cf44afea5f5fd81a1477d6b80e9474568922a0371dfb37cfc1a36477f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject' />

<img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3e106878-ed87-4ccf-897d-5c98a9d1cf70/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220823%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220823T001637Z&X-Amz-Expires=86400&X-Amz-Signature=822e08c345ba77015959b46f1b93f55124a7722f300de9050810ef36be3e77d6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject' />

 
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

