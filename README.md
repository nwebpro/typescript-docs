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
// extends er maddome apni bole dite parben je ai value gula chara onno kono value accept korbe na ai function a tar jonno apnake extends kore type bole dite hobe niche example dewa ace.

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