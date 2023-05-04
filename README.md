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