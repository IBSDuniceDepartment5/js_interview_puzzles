# Проверка строки на верное закрытие скобок
Существует 3 вида скобок, каждая их которых может быть закрытой либо открытой:
```ts
enum Bracket {
    SQUARE_OPEN = '[',
    SQUARE_CLOSE = ']',
    FIGURE_OPEN = '{',
    FIGURE_CLOSE = '}',
    ROUND_OPEN = '(',
    ROUND_CLOSE = ')',
}
```
Необходимо реализовать функцию isBracketsValid, принимающую в себя строку всех возможный значений enum 
```ts
type StringToCheck = `${Bracket[]}`

declare function isBracketsValid(brackets: StringToCheck): boolean
```
Пример передаваемых значений и результат:
```ts
let bracketsString1: StringToCheck = '[{()}]' // true
let bracketsString2: StringToCheck = '[]{}()' // true
let bracketsString3: StringToCheck = '[[})((' // false
let bracketsString4: StringToCheck = '[}' // false
```
