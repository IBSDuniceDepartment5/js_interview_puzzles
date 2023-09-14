# Создание хэш объекта по ключу элемента массива
### Напишите функцию mapArrayToHashByKey. Она принимает два аргумента -- массив объектов array и строку key.
```ts
interface Item {
    id: number;
    age: number;
    address: {
        city: string;
        zipCode: number;
    },
    name: string,
    surname: string
}
type Hash = Record<string, Item | Array<string>>

declare function mapArrayToHashByKey: Hash (data: Array<Item>, key: string);    
```
### Функция должна вернуть объект со структурой:
```ts
{
    array[0][key]: array[0],
    array[1][key]: array[2],
    ....
    _${key}s: [array[0][key], array[1][key], ... ]
}
```
### Пример данных на вход и результат:
```ts
const data: Array<Item> = [
    {
        id: 1,
        age: 25,
        address: {
            city: "New York",
            zipCode: 10001,
        },
        name: "John",
        surname: "Doe",
    },
    {
        id: 2,
        age: 30,
        address: {
            city: "Los Angeles",
            zipCode: 90001,
        },
        name: "Jane",
        surname: "Smith",
    },
];

console.log(mapArrayToHashByKey(data, "age"))

// результат:
{
    "25": {
        id: 1,
        age: 25,
        address: {
            city: "New York",
            "zipCode": 10001
        },
        name: "John",
        surname: "Doe"
    },
    "30": {
        id: 2,
        age: 30,
        address: {
            city: "Los Angeles",
            zipCode: 90001
        },
        name: "Jane",
        surname: "Smith"
    },
    "_ages": [
        "25",
        "30"
    ]
}

```
### Ограничения и гарантии:
- гарантируется, что значения ключей объектов в массиве array (и вложенных объектов) имеют только следующие типы данных:
 - string
 - number
 - null
 - undefined
 - boolean
- рекомендуемая временная сложность функции -- O(n).
- параметр array может принимать значения null или undefined - в этом случае выполнение функции не должно завершиться ошибкой
- если аргумента key нет среди ключей объектов массива array - функция должна вернуть структуру вида:
```ts
{
    _${key}s: [];
}
```