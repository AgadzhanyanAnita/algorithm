## 1. Палиндром 
Палиндромом называется строка, которая пишется одинаково слева направо и справа налево (в том числе пустая). При определении «палиндромности» строки должны учитываться только буквы и цифры. А пробелы, знаки препинания, а также регистр символов должны игнорироваться. Нужно написать функцию, которая определяет является ли строка палиндромом.

[Задача на leetcode](https://leetcode.com/problems/valid-palindrome/)

## Примеры

```
Ввод: s = “A man, a plan, a canal: Panama”
Вывод: true
 
Ввод: s = “race a car”
Вывод: false

Ввод: s = “r?a?c?e?c?a?r?”
Вывод: true

Ввод: s = “RACEcar”
Вывод: true
```

```swift
func isPalindrome(_ str: String) -> Bool {
  return true
}
```

> Компании: Яндекс

<details>
  <summary> Решение </summary>
  
  Предлагаю рассмотреть два варианта решения.
  
  Легко читаемое и краткое решение.
  1. Оставляем в строке только буквы и цифры. 
  2. Приводим все к одному регистру. 
  3. Сравниваем строку с перевернутой.
  
  Минус этого варианта в том, что по памяти алгоритм имеет сложность O(n).


  ```swift
  func isPalindrome(_ s: String) -> Bool {
    var str = s.filter {
      $0.isLetter || $0.isNumber
    }.map {
      $0.lowercased()
    }
    return str.reversed() == str
  }
  ```
  И второй вариант - это метод двух указателей. Он приоритетнее тем, что по памяти алгоритм имеет константную сложность. 
  Метод двух указателей очень эффективен при решении большого количества задач.
 
  1. В качестве двух указателей будут выступать две переменные, которые в начале хранят индексы первого и последнего элемента.
  2. Если символ не число и не буква, то пропускаем его.
  3. Сравниваем символы, приведенные к одному регистру.
  4. Смещаем указатели.

  ```swift
  func isPalindrome(_ s: String) -> Bool {
    var start = s.startIndex 
    var end = s.index(before: s.endIndex)

    while start < end {

      if !s[start].isNumber, !s[start].isLetter {  
        start = s.index(after: start)
        continue 
      }

      if !s[end].isNumber, !s[end].isLetter {  
        end = s.index(before: end)
        continue 
      }

      if s[start].lowercased() != s[end].lowercased() { return false }
      start = s.index(after: start)
      end = s.index(before: end)
    }
    return true
  }
  ```
</details>

## 2. Fuzzy Search

> Компании: Яндекс

## 3. Дано два отсортированных массива. Слить их в третий отсортированный массив.

> Компании: ВК

## 4.

## Примеры

```
Ввод: s = “)())”
Вывод: false

Ввод: s = “()(())”
Вывод: true
```

```swift
func checkCorrectness(of sequence: String) -> Bool {
  return false
}
```

> Компании: ВК

## 5.

## Примеры

```
Ввод: s = “([())]”
Вывод: false

Ввод: s = “()[]”
Вывод: true
```

```swift
func checkCorrectness(of sequence: String) -> Bool {
  return false
}
```

> Компании: ВК
