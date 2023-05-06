# Typescript documentation

## Generic Interface in Typescript
```tsx
interface ICrush <T>{
    name: string;
    husband: T;
}
interface IHusband {
    name: string;
    age: number;
}

// Use Generic Interface Example
const crush: ICrush<boolean> = {
    name: 'Madam',
    husband: true
}
// Object Type Generic Interface
const crush: ICrush<IHusband> = {
    name: 'Madam',
    husband:{
        name: 'Sir',
        age: 24
    }
}
```

## Generic Function in Typescript
```tsx
interface ICountry {
    name: string;
    population: number;
}
// Generic Arrow Function
const createArray = <T>(param: T): T[] => {
    return [param];
};

// Generic Normal Function
function createArray<T>(param: T): T[] {
    return [param];
}

const result1 = createArray<string>('Bangladesh', 'India', 'USA')
const result2 = createArray<boolean>(true)
const result1 = createArray<ICountry>(
    {
        name: 'Bangladesh', 
        population: 170000000
    },
    {
        name: 'India', 
        population: 1300000000
    },
    {
        name: 'USA', 
        population: 330000000
    }
)
```

## Constraints in Generics
```tsx
// extends er maddome apni bole dite parben je ai value gula chara onno kono value 
// accept korbe na ai function a tar jonno apnake extends kore type bole dite hobe 
// niche example dewa ace.

// My Info Type
type MyInfoType = {
    name: string;
    age: number;
    salary: number;
}

const addMeInMyCrushMind = <T extends MyInfoType> (myInfo: T) => {
    const crush = 'Madam'
    const newData = {
        ...myInfo,
        crush
    }
    return newData
}

const myInfo: MyInfoType = {
    name: 'Sir',
    age: 24,
    salary: 100000
}
const result = addMeInMyCrushMind(myInfo)

// Generic Constraints Using Key Of Part 1
type PersonType = {
    name: string;
    age: number;
    address: string;
}

// crate a union type using PersonType
type PersonTypeKeys = keyof PersonType;
const test1: PersonTypeKeys = 'name'

// Advance use case with keyof union type
function getProperty<X, Y extends keyof X>(obj: X, key: Y){
    obj[key]
}
const property = getProperty(
    {
        name: 'Mr. X',
        age: 24,
    },
    'name'
)
```

## Asynchronous TypeScript
```tsx
// Object Type Promise
interface IDataType {
    data: string;
}
const makePromise = (): Promise<IDataType> => {
    return new Promise<IDataType>((resolve, reject) => {
        const data: IDataType = 'Data is Updated'
        if(data) {
            resolve(data)
        } else {
            reject('Data is not Updated')
        }
    })
}

const getPromiseData = async(): Promise<IDataType> => {
    const data = await makePromise()
    return data
}

// String Type Promise
const makePromise = (): Promise<string> => {
    return new Promise<string>((resolve, reject) => {
        const data: string = 'Data is Updated'
        if(data) {
            resolve(data)
        } else {
            reject('Data is not Updated')
        }
    })
}

const getPromiseData = async(): Promise<string> => {
    const data = await makePromise()
    return data
}

// Fetch json Placeholder Data 
interface ITodo {
    userId: number;
    id: number;
    title: string;
    completed: boolean
}
const getData = async(): Promise<ITodo> => {
    const response = fetach('https://jsonplaceholder.typicode.com/todos/1')
    return data = await response.json()
}

const getTodoData async(): Promise<void> => {
    const result = await getData()
}
getTodoData()
```

## Conditional Types
```tsx
// a type is dependent on another type
type a = null
type c = undefined
type d = number
type b = a extends string ? string : null

// Nested Conditional rendering type
type e = a extends null 
    ? null 
    : c extends null 
    ? undefined 
    : d extends null 
    ? number 
    : null

type SheikhType = {
    wife1: string,
    wife2: string
}
type CheckProperty<T, K> = T extends keyof SheikhType ? true : false
type CheckWife = CheckProperty<SheikhType, 'wife1'> 

// Matha Kharap Kora Example
type Bandhubi = 'Fatema' | 'Tanjia' | 'Tisa'
type RemoveBandhubi<T, R> = T extends R ? never : T
type CurrentBandhubi = RemoveBandhubi<Bandhubi, 'Fatema'>

// Output
type CurrentBandhubi = 'Tanjia' | 'Tisa'
```

# Module 4 Typescript

## How to Create Class, Object , Parameter Properties
```tsx
// Create Class
class Person {
    // Parameter Properties 
    //[perameter property er maddome amra constructor er moddhe 
    //parameter declare kore ek sathe public, private, 
    //protected declare korte pari tar jonno alada kore ar type bole dite hobe na]
    constructor(public name: string, public age: number) {}
    // Create Method [Class er moddhe function create korle take method bole]
    public makePerson(): string {
        console.log(`My name is ${this.name} and I am ${this.age} years old`)
    }
}
const person = new Person('Sir', 24)
person.makePerson()
```

## Inheritence
```tsx
// Inheritance

// Person Class with common type and method
class Person {
    name: string;
    age: number;
    address: string;

    constructor(name: string, age: number, address: string) {
        this.name = name;
        this.age = age;
        this.address = address;
    }

    makeSleep(hours: number): string {
        return `This ${this.name} will sleep for ${hours} hours`
    }
}

// Teacher Class extend by person class value and method
class Teacher extends Person {
    designation: string; // different property

    constructor(name: string, age: number, address: string, designation: string) {
        super(name, age, address)
        this.designation = designation;
    }

    takeClasses(numOfClass: number): string { // different method
        return `This ${this.name} will take ${numOfClass} classes`
    }
}
const teacher1 = new Teacher('Naeem', 24, 'Dhaka', 'Web Developer')

// Student Class extend by person class value and method
class Student extends Person {
    constructor(name: string, age: number, address: string) {
        super(name, age, address)
    }
}
const student1 = new Student('Hafiz', 24, 'Dhaka')

// super use kora hoyeche karon teacher & student class parent class ke extend
// korche tay value access korar jonno super use kora hoyeche
```

# Type Guards / Type Narrowing
```tsx
// Keyof Guard
type AlphaNumeric = string | number;
function add(a: AlphaNumeric, b: AlphaNumeric): AlphaNumeric {
    if(typeof a === 'number' && typeof b === 'number') {
        return a + b
    }
    return a.toString() + b.toString()
}

// In Guard
type NormalUserType = {
    name: string;
}
type AdminUserType = {
    name: string;
    role: 'admin';
}

function getUser(user: NormalUserType | AdminUserType): string {
    if('role' in user) {
        return `I'm an admin and my role is ${user.role}`
    }
    return `I'm a normal user`
}

const normalUser: NormalUserType = {
    name: 'Hafiz'
}
const adminUser: AdminUserType = {
    name: 'Naeem',
    role: 'admin'
}

console.log(getUser(normalUser))
console.log(getUser(adminUser))

// instanceof Guard [class and object er moddhe guard add korar jonno use kore]
class Animal {
    name: string;
    constructor(name: string) {
        this.name = name;
    }

    makeSound(sound: string): string {
        return `This ${this.name} will make ${sound} sound`
    }
}

class Dog extends Animal {
    constructor(name: string) {
        super(name)
    }
    makeBark() {
        return `${this.name} will bark`
    }
}

class Cat extends Animal {
    constructor(name: string) {
        super(name)
    }
    makeMeow() {
        return `${this.name} will meow`
    }
}

function getAnimal(animal: Animal): string {
    if(animal instanceof Dog) {
        return animal.makeBark()
    }
    if(animal instanceof Cat) {
        return animal.makeMeow()
    }
    return animal.makeSound('some')
}

const animal1 = new Dog('Smart Dog') // instance of Dog
const animal2 = new Cat('Cute Cat') // instance of Cat

console.log(getAnimal(animal1))
console.log(getAnimal(animal2))

```

# Typescript Practice
## 1 Convert the following JavaScript array into a TypeScript tuple
```tsx
const userInfo = [101, "Ema", "John", true,  , "2023"];
```
```tsx
// Solution
const userInfo: [number, string, string, boolean, string | undefined, string] = [101, "Ema", "John", true,  , "2023"];
```

## 2 Write a TypeScript function that takes in two arrays of numbers as parameters. The function should compare the elements in both arrays and return a new array that contains only the elements that are present in both arrays.
```tsx
const array1 = [1, 2, 3, 4, 5];
const array2 = [2, 4, 6, 8, 10];
```
```tsx
// Solution
const commonElements = (arr1: number[], arr2: number[]): number[] => {
    const common: number[] = [];
    arr1.forEach((num) => {
        if(arr2.includes(num)) {
            common.push(num)
        }
    })
    return common;
}

const array1 = [1, 2, 3, 4, 5, 6, 10];
const array2 = [2, 4, 6, 8, 10];
const result = commonElements(array1, array2);
console.log(result);
```

## 3 You have an interface for ``Product``, containing the product's id, name, price, and category. You want to filter an array of Products based on a specific criterion and value.
```tsx
// Solution
//Write a TypeScript generic function that takes this array, a criterion ,
// and returns a new array containing only the products that match the 
// given criterion and value. Use a generic type parameter in the function 
// signature to ensure type safety.
interface Product {
  id: number;
  name: string;
  price: number;
  category: string;
}

const productsArray: Product[] = [
  { id: 1, name: "Product 1", price: 10, category: "Mobile" },
  { id: 2, name: "Product 2", price: 20, category: "Laptop" },
  { id: 3, name: "Product 3", price: 30, category: "Mobile" },
  { id: 4, name: "Product 4", price: 40, category: "Mac Book" },
];

const filterProductsByCriterion = <T extends keyof Product>(
  products: Product[],
  criterion: T,
  value: Product[T]
): Product[] => {
  return productsArray.filter(product => product[criterion] === value);
}

const result = filterProductsByCriterion(products, "category", "Mobile");
console.log(result);
```

## 4 Suppose you have an array of tuples, where each tuple represents a product and contains the product name, price, and quantity. Write a TypeScript function that calculates the total cost of all the products in the array, using a generic type for the tuple and a type alias for the array.
```tsx
// Solution
type ProductTuple = [string, number, number];
type Products = ProductTuple[];

const products: Products = [
  ["Product 1", 10, 2],
  ["Product 2", 20, 4],
  ["Product 3", 30, 6],
  ["Product 4", 40, 8],
];

const calculateTotalCost = (products: Products): number => {
  let total = 0;
  products.forEach((product) => {
    total += product[1] * product[2];
  });
  return total;
};

const result = calculateTotalCost(products);
console.log(result);
```

## 5 Suppose you have an array of numbers in TypeScript, and you want to find the sum of all the even numbers in the array. How would you approach this problem and write code to solve it?
```tsx
// Solution
const numbers: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9];
const sumOfEvenNumbers = (numbers: number[]): number => {
  let sum = 0;
  numbers.forEach((num) => {
    if (num % 2 === 0) {
      sum += num;
    }
  });
  return sum;
};

const result = sumOfEvenNumbers(numbers);
console.log(result);
```

## 6 Create an interface called ``Person`` that includes properties for name (string), age (number), and email (string). Then create an array of Person objects and write a function that takes the array and a string email as parameters, and returns the Person object that matches the email or null if no match is found.
```tsx
// Solution
interface Person {
  name: string;
  age: number;
  email: string;
}

const people: Person[] = [
    { name: 'Naeem', age: 25, email: 'test@gmail.com' },
    { name: 'Rahim', age: 26, email: 'test1@gmail.com' },
    { name: 'Karim', age: 27, email: 'test2@gmail.com' }
]

const checkPersonByEmail = (people: Person[], email: string): Person | null => {
    let person: Person | null = null;
    people.forEach((p) => {
        if(p.email === email) {
            person = p;
        }
    })
    return person;
}

const result = checkPersonByEmail(people, 'test5@gmail.com');
if(result) {
    console.log(result);
} else {
    console.log('No person found');
}
```