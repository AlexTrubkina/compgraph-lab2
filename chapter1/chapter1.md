## Задание 1

Напишите однофайловую программу (с именем main.cpp), которая запрашивает у пользователя два целых числа, складывает их, а затем выводит результат. В программе должно быть 3 функции:

   функция readNumber(), которая запрашивает у пользователя целое число, а затем возвращает его в main();

   функция writeAnswer(), которая выводит результат на экран. Функция должна быть без возвращаемого значения и иметь только один параметр;

   функция main(), которая соединяет всё и вся.

``` cpp
#include <iostream>

int readNumber(){
  std:cout <<"Введите число: " << std::endl;
  std::cin >> number;
  return number;
}

void writeAnswer(int result){
  std:cout <<"Результат вычислений: " << result <<std::endl;
}

int main(){
  num_1 = readNumber();
  num_2 = readNumber();
  result = num_1 + num_2;
  writeAnswer(result);
  return result;
}

```

## Задание 2

Измените программу из задания №1 так, чтобы функции readNumber() и writeAnswer() находились в отдельном файле io.cpp. Используйте предварительные объявления для доступа к этим функциям с функции main().

файл io.cpp:
``` cpp
#include <iostream>

int readNumber(){
  std:cout <<"Введите число: " << std::endl;
  std::cin >> number;
  return number;
}

void writeAnswer(int result){
  std:cout <<"Результат вычислений: " << result <<std::endl;
}

```

файл main.cpp

```cpp
int readNumber();
void writeAnswer(int x);

int main(){
  num_1 = readNumber();
  num_2 = readNumber();
  result = num_1 + num_2;
  writeAnswer(result);
  return result;
}
```

## Задание 3

Измените программу из задания №2 так, чтобы она использовала заголовочный файл io.h для доступа к функциям (вместо использования предварительных объявлений). Убедитесь, что ваш заголовочный файл использует header guards.

файл io.h

```cpp

#ifndef IO_H
#define IO_H
 
int readNumber();
void writeAnswer(int x);
 
#endif

```

файл io.cpp:
``` cpp
#include <iostream>

int readNumber(){
  std:cout <<"Введите число: " << std::endl;
  std::cin >> number;
  return number;
}

void writeAnswer(int result){
  std:cout <<"Результат вычислений: " << result <<std::endl;
}

```

файл main.cpp

```cpp
#include "io.h"

int main(){
  num_1 = readNumber();
  num_2 = readNumber();
  result = num_1 + num_2;
  writeAnswer(result);
  return result;
}
```
