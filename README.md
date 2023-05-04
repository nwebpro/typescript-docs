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