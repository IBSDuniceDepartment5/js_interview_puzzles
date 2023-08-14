# Поиск узла в дереве элементов

Дано дерево элементов вида:
```ts
interface Element {
    id: number,
    name: string,
    children: Tree
}

type Tree = Array<Element>
```
Необходимо написать функцию `findNodeByTreeId`, принимающую дерево и айди элемента и возвращающую сам элемент, в случае, если такого элемента нет в дереве, то функция должна вернуть `null`
Задача должна быть решена и с помощью рекурсии и с помощью циклов c аккумуляцией значений    

Пример передаваемых значений и результат:

```ts
declare function findElementById(tree: Tree, id: number)

let tree: Tree = [
  {
    id: 1,
    name: 'Root',
    children: [
      {
        id: 2,
        name: 'Child 1',
        children: []
      },
      {
        id: 3,
        name: 'Child 2',
        children: [
          {
            id: 4,
            name: 'Grandchild',
            children: []
          }
        ]
      }
    ]
  }
];

let idToFind = 4;

let result = findElementById(tree, idToFind);
console.log(result); // вывод: { id: 4, name: 'Grandchild', children: [] }
```
